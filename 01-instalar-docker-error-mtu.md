# 01 - Instalar Docker en Ubuntu: error de SSL por el MTU

**Fecha:** 23/11/2026

## Qué queríamos

Instalar Docker en una máquina virtual Ubuntu (creada con Multipass en el Mac) para seguir el curso de Docker.

```bash
curl -fsSL https://get.docker.com | bash
```

## Qué pasó

La instalación fallaba siempre con este error:

```
SSL connection failed: unexpected eof while reading
E: Package 'docker-ce' has no installation candidate
```

La máquina no conseguía descargar los paquetes de Docker.

## Por qué pasaba

La máquina virtual enviaba paquetes de red de **1500 bytes** (es el **MTU**, el tamaño máximo de paquete).
Mi red no deja pasar paquetes tan grandes, así que las descargas se cortaban a mitad.

Lo comprobamos con `ping`:

```bash
ping -M do -s 1472 -c 3 8.8.8.8   # paquete de 1500 bytes → falla
ping -M do -s 1372 -c 3 8.8.8.8   # paquete de 1400 bytes → funciona
```

## Cómo lo solucionamos

**1. Bajamos el MTU a 1400 y Docker se instaló:**

```bash
ip link set dev enp0s1 mtu 1400
apt-get update
apt-get install -y docker-ce docker-ce-cli containerd.io \
  docker-compose-plugin docker-buildx-plugin
systemctl enable --now docker
```

**2. Lo dejamos fijo para que no se pierda al reiniciar:**

```bash
cat > /etc/netplan/99-mtu.yaml <<'EOF'
network:
  version: 2
  ethernets:
    eth0:
      mtu: 1400
EOF
chmod 600 /etc/netplan/99-mtu.yaml
reboot
```

**3. Comprobamos que funciona:**

```bash
sudo docker run hello-world
```

Resultado: `Hello from Docker!` ✅

## Si vuelve a pasar: pasos rápidos

1. **¿Hay internet?** → `ping -c 3 google.com`
2. **¿Funciona HTTPS?** → `curl -I https://download.docker.com`
3. **¿Pasan los paquetes grandes?** → `ping -M do -s 1472 -c 3 8.8.8.8` (si falla, prueba `ping -M do -s 1372 -c 3 8.8.8.8`)
4. **Si el pequeño pasa y el grande no** → `ip link set dev eth0 mtu 1400`
5. **Prueba otra vez** → `apt-get update`
6. **Si ahora funciona** → déjalo fijo con el archivo `99-mtu.yaml` (paso 2 de arriba)

## Lo que aprendí

- Si las cosas pequeñas funcionan y las descargas grandes fallan, hay que revisar el **MTU**.
- Antes de instalar otra cosa para salir del paso, conviene buscar la causa real.
