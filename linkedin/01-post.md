Qué es el MTU
Es el tamaño máximo de "paquete" que puede pasar por la red. Es como el buzón en Black Friday: las cartas sí entran, pero el regalo en paquete no.

Así lo resolví instalando Docker en Ubuntu, por etapas:

━━━━━━━━━━
ETAPA 1 · El error

Escribes:
curl -fsSL https://get.docker.com | bash

Te sale algo así:
SSL connection failed: unexpected eof while reading
E: Package 'docker-ce' has no installation candidate

La descarga se corta a mitad. Vamos a ver si es el MTU.

━━━━━━━━━━
ETAPA 2 · Comprobar si es el MTU

Escribe:
ping -M do -s 1472 -c 3 8.8.8.8

Te saldrá algo así:
3 packets transmitted, 0 received, 100% packet loss

→ Si sale 100% packet loss: los paquetes grandes no pasan. Es el MTU. Sigue a la etapa 3.
→ Si sale 0% packet loss: el MTU está bien y el problema es otro. Búscalo en mi página (enlace abajo).

━━━━━━━━━━
ETAPA 3 · Bajar el MTU

Primero mira cómo se llama tu tarjeta de red. Escribe:
ip link

Te saldrá algo así:
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 ...
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 ...

→ "lo" no te interesa, es interna del sistema.
→ Tu tarjeta es la de la línea 2, justo después del número. En este ejemplo se llama eth0 (puede llamarse distinto, como enp0s1).
→ Al lado verás mtu 1500. Ese es el que vamos a bajar.

Ahora escribe, con el nombre de tu tarjeta:
sudo ip link set dev eth0 mtu 1400

No sale nada. Es normal. Si vuelves a escribir ip link, verás mtu 1400.

━━━━━━━━━━
ETAPA 4 · Comprobar que ya descarga

Escribe:
sudo apt-get update

Te saldrá algo así:
Get:1 https://download.docker.com/linux/ubuntu ... InRelease [32.5 kB]

→ Si sale Get: sin errores: ya descarga. Sigue a la etapa 5.
→ Si sigue saliendo SSL connection failed: quita la VPN si tienes una, o prueba con mtu 1300.

━━━━━━━━━━
ETAPA 5 · Instalar y probar

Escribe:
curl -fsSL https://get.docker.com | bash
sudo docker run hello-world

Te saldrá:
Hello from Docker!

Funciona.

━━━━━━━━━━
ETAPA 6 · Dejarlo fijo

El cambio de la etapa 3 se pierde al reiniciar. Para dejarlo fijo, crea /etc/netplan/99-mtu.yaml con esto (cambia eth0 por el nombre de tu tarjeta):

network:
  version: 2
  ethernets:
    eth0:
      mtu: 1400

Y escribe:
sudo netplan generate && sudo reboot

━━━━━━━━━━

Lo que aprendí: un error de SSL no siempre es un problema de SSL. A veces el problema no es el paquete, es el buzón.

Si te sale otro error, búscalo en mi página, donde voy documentando cada problema de Docker y cómo lo resuelvo:
https://github.com/jventurapedro/docker-problemas-y-soluciones

#Docker #DevOps #Linux #Networking
