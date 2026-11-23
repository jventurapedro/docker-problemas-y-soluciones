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
- **Mismo contenido en todas partes.** Notion y GitHub llevan el mismo texto. LinkedIn es un resumen.
- **Siempre se actualiza el índice** al añadir un capítulo.

## 2. Plantilla de cada capítulo (estilo del 01)

```
# NN - Título

**Fecha:** DD/MM/AAAA

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

- **Un post por capítulo**, después de subirlo a GitHub.
- **Estructura del post:**
  1. Gancho (1 línea): el problema contado de forma curiosa.
  2. Qué quería hacer (1–2 líneas).
  3. El error (1 línea).
  4. Cómo lo investigué (3–5 pasos cortos).
  5. La causa (1–2 líneas, fácil).
  6. La solución (1 línea).
  7. Lo que aprendí (2–3 puntos).
  8. Enlace al capítulo en GitHub.
  9. Hashtags: `#Docker #DevOps #Linux` + 2–3 del tema.
- Versión en **español** e **inglés**.
- Lo publica Pedro.

## 6. Orden para publicar

1. Resolver el problema.
2. Escribir el capítulo con la plantilla.
3. Subirlo a **Notion** (subpágina + fila en el índice).
4. Subirlo a **GitHub** (archivo + fila en el README).
5. Publicar en **LinkedIn** con el enlace de GitHub.
