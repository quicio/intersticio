# INTERSTICIO

Publicación digital editorial sobre los espacios entre disciplinas:
tecnología, inteligencia artificial, arte, diseño, ciencia, cultura digital,
música, comunidades creativas y futuros emergentes.

> Las ideas más interesantes suelen aparecer en los intersticios: los
> espacios donde disciplinas distintas entran en contacto.

Sitio construido con **Jekyll** y desplegado en **GitHub Pages**.

## Estructura del proyecto

```
.
├── .specify/          # Especificación editorial (spec kit)
├── .plan/             # Plan técnico
├── .github/workflows/ # CI/CD
├── _config.yml        # Configuración de Jekyll
├── _data/             # Datos editoriales
├── _includes/         # Componentes reutilizables
├── _layouts/          # Plantillas
├── _observaciones/    # Colección 1 — notas cortas
├── _artefactos/       # Colección 2 — análisis de obras
├── _laboratorios/     # Colección 3 — procesos propios
├── _resonancias/      # Colección 4 — ensayos largos
├── _derivadas/        # Colección 5 — recapitulaciones
├── assets/            # CSS, favicon, imágenes
├── index.html         # Portada
├── archivo.html       # Archivo cronológico
└── sobre.html         # Manifiesto
```

## Desarrollo local

Requisitos: Ruby 3.x, Bundler.

```bash
bundle install
bundle exec jekyll serve
```

El sitio se servirá en `http://localhost:4000`.

## Crear contenido

Para añadir una pieza, crea un archivo Markdown en la carpeta de la
colección correspondiente con el siguiente frontmatter:

```yaml
---
title: "Título de la pieza"
coleccion: observaciones
fecha: 2024-XX-XX
autor: "INTERSTICIO"
resumen: "Una o dos frases. Aparece en portada y OG."
etiquetas: [campo1, campo2]
carta: "Línea editorial opcional al abrir la pieza."
---

Cuerpo del artículo en Markdown.
```

Las cinco colecciones disponibles son:

- `observaciones` — piezas cortas, 300–800 palabras
- `artefactos` — análisis de obras/herramientas/publicaciones
- `laboratorios` — procesos propios
- `resonancias` — ensayos largos
- `derivadas` — recapitulaciones, índices, estados de la cuestión

## Despliegue

El sitio se publica automáticamente en GitHub Pages al hacer push a
`main` (workflow `.github/workflows/jekyll.yml`).

La URL queda en `https://<usuario>.github.io/intersticio/`. Para un
dominio propio, añade un archivo `CNAME` en la raíz.

## Decisiones técnicas

- **Sin JavaScript en producción.** Toda la interactividad se resuelve
  con CSS o no existe.
- **Sin trackers, sin analytics.** La atención del visitante no es un
  recurso a monetizar.
- **Markdown + Git como CMS.** No hay interfaz intermedia; cualquier
  persona con `git` puede contribuir.

## Licencia

El código del sitio es open source. El contenido editorial se publica
bajo la licencia que elijas para tu contexto. Por defecto, sugerimos
CC BY-NC-SA 4.0 para los textos.

## Más

- [Especificación editorial completa](.specify/spec.md)
- [Plan técnico](.plan/plan.md)
