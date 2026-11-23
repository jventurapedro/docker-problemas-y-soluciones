# REGLAS — Docker - Problemas y Soluciones

Este archivo manda. Todo lo que se publique (Notion, GitHub, LinkedIn) sigue estas reglas para que todos los capítulos sean iguales. El modelo es el capítulo **01**.

---

## 1. Reglas generales

- **Lenguaje sencillo.** Frases cortas, fáciles de leer y entender. Nada de palabras raras.
- **Problemas reales.** Solo cosas que nos han pasado de verdad, con los comandos y errores reales.
- **Numeración:** 01, 02, 03… Nunca se salta ni se repite un número.
- **Título del capítulo:** `NN - Qué queríamos hacer: cuál fue el error`
  - Ejemplo: `01 - Instalar Docker en Ubuntu: error de SSL por el MTU`
- **Fecha:** formato `DD/MM/AAAA`.
- **Entorno y error arriba del todo:** para que quien llegue desde Google (junior, pleno o senior) sepa al momento si es su caso.
- **Mismo contenido en todas partes.** Notion y GitHub llevan el mismo texto. LinkedIn va por etapas (punto 5).
- **Siempre se actualiza el índice** al añadir un capítulo.

## 2. Plantilla de cada capítulo (estilo del 01)

```
# NN - Título

**Fecha:** DD/MM/AAAA
**Entorno:** sistema · versión · dónde corre (ej. Ubuntu 26.04 · Multipass en Mac · Docker 29.10)
**Error:** el mensaje de error exacto, tal cual sale

## Qué queríamos
Una o dos frases + el comando que íbamos a usar.

## Qué pasó
El error real (copiado tal cual en un bloque de código) + una frase explicándolo.

## Por qué pasaba
La causa explicada fácil + el comando con el que lo comprobamos.

## Cómo lo solucionamos
Pasos numerados (1, 2, 3…) con sus comandos.
El último paso siempre es comprobar que funciona y su resultado ✅.

## Si vuelve a pasar: pasos rápidos
Lista numerada corta: ¿qué compruebo? → comando.

## Lo que aprendí
2 o 3 puntos, una frase cada uno.

## Referencias
Enlaces a la documentación oficial que hemos usado.
```

---

## 3. NOTION

- **Página principal:** `Docker - Problemas y Soluciones` (icono de ballena).
- Arriba, una frase: *Problemas reales que me encuentro aprendiendo Docker y cómo los soluciono.*
- **Índice:** tabla con columnas `Nº | Fecha | Problema`. Una fila por capítulo.
- **Capítulos:** cada uno es una **subpágina** de la principal, con el título `NN - Título`.
- El contenido de la subpágina sigue la plantilla del punto 2.
- Los comandos y errores siempre en **bloques de código**.

## 4. GITHUB

- **Repo:** `docker-problemas-y-soluciones` (público).
- **Archivos:**
  - `README.md` → título, frase de presentación e índice (`Nº | Fecha | Problema`, con enlace a cada capítulo).
  - `REGLAS.md` → este archivo. **Tiene prioridad** sobre cualquier otra forma de escribir.
  - Un archivo por capítulo: `NN-nombre-corto-en-minusculas.md`
    - Ejemplo: `01-instalar-docker-error-mtu.md`
- **Commit:** `Capítulo NN: título corto`
- El texto del capítulo es **el mismo** que en Notion.

## 5. LINKEDIN

Cuando Pedro diga **"hacemos el post"**, se escribe con este patrón. El modelo es el post del capítulo 01 (`linkedin/01-post.md`).

**Estilo**
- Español de Madrid, sencillo y directo.
- Emojis solo los necesarios: ❌ y ✅ como mucho.
- Solo en español (en inglés solo si Pedro lo pide).
- Lo publica Pedro.

**Estructura**

1. **Qué es [el concepto]**
   Una frase que lo define + una comparación con algo cotidiano de esas fechas (ejemplo: el buzón de casa en pleno Black Friday).

2. **Así lo resolví [haciendo X], por etapas:**

3. **Etapas**, separadas por `━━━━━━━━━━`. Cada una con este formato:

```
ETAPA N · Título corto

Escribe:
(comando)

Te saldrá algo así:
(salida real copiada del terminal)

→ Si sale X: qué significa. Sigue a la etapa N.
→ Si sale Y: qué hacer en ese caso.
```

   - Si un comando necesita un dato (por ejemplo, el nombre de la tarjeta de red), se explica cómo sacarlo y cómo leer lo que sale.
   - Si un comando no muestra nada, se dice: "No sale nada. Es normal."
   - Orden habitual: El error → Comprobar la causa → Arreglarlo → Comprobar que funciona → Instalar y probar → Dejarlo fijo.

4. **Lo que aprendí:** una frase que cierra con la comparación del principio.

5. **Cierre:** "Si te sale otro error, búscalo en mi página, donde voy documentando cada problema de Docker y cómo lo resuelvo:" + enlace al repo.

6. **Hashtags:** `#Docker #DevOps #Linux` + 1 o 2 del tema.

## 6. Orden para publicar

1. Resolver el problema.
2. Escribir el capítulo con la plantilla.
3. Subirlo a **Notion** (subpágina + fila en el índice).
4. Subirlo a **GitHub** (archivo + fila en el README).
5. Escribir el post de **LinkedIn** con el patrón del punto 5. Se guarda solo en GitHub (`linkedin/NN-post.md`), no en Notion. Pedro lo publica.
