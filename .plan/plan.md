# INTERSTICIO — Plan técnico

> Plan derivado de `.specify/spec.md`. Describe la implementación concreta.

---

## 1. Stack

- **Generador:** Jekyll 4.3
- **Ruby:** 3.2 (imagen Docker oficial `jekyll/jekyll` para build local y CI)
- **Hosting:** GitHub Pages
- **CI:** GitHub Actions (workflow `pages-build-deployment`)
- **CSS:** Un solo archivo `assets/css/main.css` con custom properties, sin
  preprocesador
- **JS:** Cero. Sin frameworks. Sin analytics invasivos. Si se necesita
  interactividad, se delega a HTML/CSS nativo.
- **Fuentes:** Google Fonts vía `<link>` con `display=swap` y `preconnect`

### Plugins Jekyll (todos compatibles con GitHub Pages)

- `jekyll-feed` — RSS
- `jekyll-sitemap` — sitemap
- `jekyll-seo-tag` — meta tags
- `jekyll-paginate` — paginación del archivo (si crece)

### Plugins NO usados

- Comentarios (sin Disqus/Hyvor/etc.)
- Búsqueda cliente (innecesario al inicio)
- CMS headless (Markdown + git es el CMS)
- Tailwind, Bootstrap, Bulma (CSS escrito a mano)

---

## 2. Estructura de archivos

```
intersticio/
├── .github/
│   └── workflows/
│       └── jekyll.yml
├── .gitignore
├── 404.html
├── Gemfile
├── README.md
├── _config.yml
├── _data/
│   └── editorial.yml          # línea editorial, créditos
├── _includes/
│   ├── footer.html
│   ├── header.html
│   ├── nav.html
│   ├── article-card.html
│   ├── article-meta.html
│   ├── pagination.html
│   └── seo.html
├── _layouts/
│   ├── default.html
│   ├── home.html
│   ├── page.html
│   ├── article.html
│   ├── collection.html
│   └── archive.html
├── _sass/                      # (opcional) sólo si CSS crece
├── assets/
│   ├── css/
│   │   └── main.css
│   ├── favicon.svg
│   └── img/                    # imágenes editorial, si las hay
├── _observaciones/             # colección 1
├── _artefactos/                # colección 2
├── _laboratorios/              # colección 3
├── _resonancias/               # colección 4
├── _derivadas/                 # colección 5
├── index.html                  # portada
├── archivo.html
├── sobre.html
├── feed.xml                    # generado por jekyll-feed, ignorar en git
└── sitemap.xml                 # generado por jekyll-sitemap
```

---

## 3. Convenciones de contenido

### 3.1 Frontmatter común

```yaml
---
title: "Título de la pieza"
coleccion: observaciones
fecha: 2024-09-12
autor: "INTERSTICIO"
resumen: "Una frase que aparece en listados y OG."
etiquetas: [campo1, campo2]
carta: "Línea editorial opcional al abrir la pieza."
---
```

### 3.2 Citas en bloque

```markdown
> Esto es una cita.
> — Atribución
```

### 3.3 Notas al margen

Se implementa con `<aside class="marginalia">…</aside>`. En mobile colapsa
debajo del párrafo. No se usa JavaScript.

### 3.4 Imágenes

```markdown
![Pie de foto](/assets/img/nombre.jpg)
```

Las imágenes se sirven desde `assets/img/`, opcionalmente con `responsive_image`
o el helper nativo de Jekyll `{{ page.image }}` con `srcset` calculado a mano.

---

## 4. Sistema de layouts

### 4.1 `default.html`

Estructura raíz: `<head>` con SEO, header, `{{ content }}`, footer. Define
bloques para `title`, `description`, `og_image`.

### 4.2 `home.html`

Renderiza el hero editorial, sección de "Observaciones recientes", listado
mixto de piezas recientes, una "Pieza destacada" opcional.

### 4.3 `article.html`

Envuelve un documento de colección. Hero con título, fecha, colección,
resumen. Cuerpo con tipografía editorial. Pie con metadatos, enlaces a
etiquetas, "leer siguiente" opcional.

### 4.4 `collection.html`

Lista de una colección. Título, descripción de la colección, lista de piezas.

### 4.5 `archive.html`

Archivo cronológico agrupado por año y mes.

### 4.6 `page.html`

Para páginas estáticas (sobre, 404, etc.).

---

## 5. CSS — Estrategia

- Un único `main.css` con estructura:
  1. Custom properties (tokens)
  2. Reset minimalista
  3. Tipografía base
  4. Layout (header, nav, footer, grid principal)
  5. Componentes (article-card, cita, marginalia, etiquetas)
  6. Tipografía editorial para artículos
  7. Responsive

- Sin `@import` ni frameworks
- `prefers-color-scheme: dark` evaluado más adelante (no en MVP)

---

## 6. SEO

- `jekyll-seo-tag` para meta tags
- Open Graph image por defecto: SVG editorial
- `robots.txt` permitiendo todo, apuntando al sitemap
- `feed.xml` con contenido completo por pieza (configurable en `_config.yml`
  de `jekyll-feed`)

---

## 7. CI / Deploy

Workflow `.github/workflows/jekyll.yml`:

```yaml
name: Build and deploy Jekyll
on:
  push:
    branches: [main]
  workflow_dispatch:
permissions:
  contents: read
  pages: write
  id-token: write
concurrency:
  group: pages
  cancel-in-progress: false
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v5
      - uses: actions/jekyll-build-pages@v1
        with:
          source: .
      - uses: actions/upload-pages-artifact@v3
  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - id: deployment
        uses: actions/deploy-pages@v4
```

---

## 8. Roadmap mínimo

1. Estructura + scaffold
2. Identidad visual base (CSS + tipografía)
3. Layouts + includes
4. Colecciones configuradas
5. Una pieza de ejemplo por colección
6. Portada + archivo + sobre
7. RSS + sitemap + SEO
8. CI + deploy

---

## 9. Decisiones explícitas (ADR light)

- **Sin JS** — la interactividad se delega a CSS o no existe. Cumple "calma".
- **Markdown + git** — el CMS. Sin interfaces intermedias. Cualquier persona
  con `git` puede contribuir.
- **Google Fonts** — auto-hospedaje se puede añadir más adelante. La elección
  de Fraunces + Inter es estable y ampliamente cacheada.
- **Sin tema de terceros** — un tema Jekyll existente condicionaría la voz
  visual. Se escribe a mano.
- **Colecciones sobre categorías** — Jekyll trata las colecciones como
  ciudadanos de primera, lo que respeta el modelo editorial de INTERSTICIO.
