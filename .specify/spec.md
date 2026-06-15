# INTERSTICIO — Especificación

> Spec generada con el flujo `/spec-kit` de GitHub. Esta es la fuente de verdad
> editorial. El plan técnico en `.plan/plan.md` se deriva de este documento.

---

## 1. Declaración editorial

**INTERSTICIO** es una publicación digital dedicada a explorar los espacios
entre disciplinas: tecnología, inteligencia artificial, arte, diseño, ciencia,
cultura digital, música, comunidades creativas y futuros emergentes.

**Tesis central:**

> Las ideas más interesantes suelen aparecer en los intersticios: los espacios
> donde disciplinas distintas entran en contacto.

**No es:** un blog tecnológico, una revista de noticias, un newsletter de
productividad, una publicación de marketing, un medio依附ado a una industria.

**Es:** un archivo vivo de observaciones, conexiones, artefactos e ideas en
desarrollo. Una publicación cultural independiente de alta calidad.

---

## 2. Tono y referencias

Lectores implícitos: lectores de **Monocle**, **Aeon**, **Nautilus**,
publicaciones del **MIT Media Lab**, revistas culturales independientes,
cuadernos de investigación contemporáneos.

El tono combina:

- Curiosidad intelectual
- Exploración
- Profundidad
- Calma
- Descubrimiento
- Conexiones inesperadas

### Lo que se evita explícitamente

- Estética startup
- Marketing y growth hacking
- Lenguaje de productividad
- Dashboards
- SaaS
- Lenguaje corporativo
- Clickbait
- "Aquí tienes 5 consejos para…"
- Listas optimizadas para SEO
- Hype sobre AI como destino

### Lo que se busca

- Una pieza que se lee como ensayo
- Referencias cruzadas entre campos
- Atención al contexto histórico
- Citas extensas cuando aportan
- Reconocer lo que no se sabe
- Permitir la duda

---

## 3. Colecciones editoriales

INTERSTICIO organiza su contenido en cinco colecciones. Cada una responde a una
pregunta distinta y tiene un cadencia propia.

### 3.1 Observaciones (`_observaciones/`)

> Piezas cortas, 300–800 palabras. Notas de campo, hallazgos, lecturas, una
> idea que merece desarrollo pero no un artículo completo.

Pregunta implícita: *¿qué noté hoy?*

Cadencia: alta. Frecuencia semanal o quincenal.

### 3.2 Artefactos (`_artefactos/`)

> Análisis de una obra, herramienta, instalación, pieza musical, software,
> publicación, exposición. Algo externo que se examina con detenimiento.

Pregunta implícita: *¿qué existe y por qué importa?*

Cadencia: media. Mensual.

### 3.3 Laboratorios (`_laboratorios/`)

> Documentación de procesos propios: prototipos, experimentos, derivas de
> investigación, lecturas en curso, herramientas en construcción.

Pregunta implícita: *¿qué estoy construyendo y qué aprendo?*

Cadencia: media-baja. Quincenal o mensual.

### 3.4 Resonancias (`_resonancias/`)

> Ensayos largos, 2000–5000 palabras. Conexiones entre campos, lectura
> profunda de un autor, genealogías, futuros especulativos con base histórica.

Pregunta implícita: *¿qué conexiones aparecen cuando me detengo?*

Cadencia: baja. Mensual o bimestral.

### 3.5 Derivadas (`_derivadas/`)

> Recopilaciones, índices comentados, antologías breves, "estados de la
> cuestión", bibliografías en movimiento.

Pregunta implícita: *¿qué se está movando en un campo?*

Cadencia: baja. Trimestral o cuando el campo lo pida.

---

## 4. Estructura del sitio

```
/                 Portada editorial
/archivo/         Archivo cronológico completo
/colecciones/     Índice de colecciones
/colecciones/<x>/ Página de cada colección
/<coleccion>/<slug>/ Artículo individual
/sobre/           Manifiesto y declaración
/rss.xml          Feed RSS
/sitemap.xml      Sitemap
/404.html         Error 404
```

### 4.1 Portada

La portada **no comunica "publicamos contenido"**. Comunica **"estamos
investigando algo"**.

Composición:

1. **Bloque de identidad**
   - Palabra: `INTERSTICIO`
   - Subtítulo: *"Exploraciones entre tecnología, arte, ciencia y cultura."*
   - Línea editorial corta (cambia con cada número / estación)
2. **Observaciones recientes** — tres piezas cortas, formato denso
3. **Últimas piezas** — mezcla de colecciones, ordenadas por fecha
4. **Una pieza destacada** — resonancia o laboratorio, formato largo

Sin tarjetas típicas de blog. Cada entrada es un bloque editorial con
jerarquía tipográfica fuerte y espacio negativo generoso.

### 4.2 Artículo

Diseño centrado en la lectura.

- Ancho de columna cómodo (~ 62–68 caracteres por línea)
- Tipografía serif para el cuerpo
- Numeración de secciones discreta
- Citas en bloque con tratamiento editorial
- Notas al margen opcionales (`<aside>` o sintaxis kramdown)
- Imágenes grandes pero sobrias, con pie de foto
- Sin widgets sociales flotantes
- Al pie: colección, etiquetas, fecha, "leer siguiente" opcional

### 4.3 Archivo

Vista cronológica agrupada por año y mes. Sin filtros caóticos. Una columna
limpia. Es la sala de máquinas de la publicación.

### 4.4 Sobre

Texto del manifiesto. Sin foto del equipo, sin "escríbenos", sin CTAs.
Una declaración de intenciones en una columna estrecha.

---

## 5. Identidad visual

### 5.1 Tono visual

Inspiraciones: revistas editoriales contemporáneas, diseño suizo, publicaciones
académicas elegantes, libros de ensayo.

### 5.2 Tipografía

- **Serif (lectura):** *Fraunces* — serif de display con personalidad
  editorial, excelente para lectura larga. Pesos: 300, 400, 500, 600.
- **Sans (navegación, UI):** *Inter* — sans sobria, muy legible, trazo
  neutro. Pesos: 400, 500, 600.
- **Mono (marcas, metadatos):** *JetBrains Mono* — para etiquetas, fechas,
  números de colección.

Ambas serif y sans se cargan desde Google Fonts (auto-hospedaje posible más
adelante). La mono opcional.

### 5.3 Paleta

Tonos neutros, casi monocromos. Acento único.

| Token            | Valor     | Uso                                |
| ---------------- | --------- | ---------------------------------- |
| `--ink`          | `#1a1a1a` | Texto principal                    |
| `--ink-soft`     | `#4a4a4a` | Texto secundario                   |
| `--ink-mute`     | `#7a7a7a` | Metadatos, fechas, etiquetas       |
| `--paper`        | `#f7f5f0` | Fondo principal (off-white cálido) |
| `--paper-soft`   | `#efece5` | Fondo secundario, separadores      |
| `--rule`         | `#d8d4c8` | Líneas finas, bordes               |
| `--accent`       | `#8a3a2a` | Acento editorial (terracota oscuro) |
| `--accent-soft`  | `#b8694f` | Acento en hover, marcas            |

`--paper` se aleja del blanco puro para reducir fatiga visual y evocar papel
impreso. El acento terracota se usa con moderación: nómeros de colección,
líneas, marcas de párrafo.

### 5.4 Sistema de espaciado

Escala basada en 8px. Líneas finas de 1px en `--rule`. Bordes redondeados
mínimos (radio 2–4px). Sin sombras pronunciadas. Sin gradientes. Sin glass.

### 5.5 Lo que no se hace

- Gradientes futuristas
- Neón
- Glassmorphism
- Animaciones excesivas
- Estética crypto
- Estética AI startup (logo de sparkle, gradient morado, etc.)

---

## 6. Navegación

Cabecera minimalista:

```
INTERSTICIO                                          Archivo  Sobre  RSS
```

En móvil: hamburguesa ligera que abre un panel sobrio, sin animación de
"slide-in" cinemática.

Pie de página:

```
INTERSTICIO · 2024–        Observaciones  Artefactos  Laboratorios  Resonancias  Derivadas
```

---

## 7. Metadatos y SEO

Cada artículo lleva frontmatter con:

```yaml
---
title:
coleccion: observaciones | artefactos | laboratorios | resonancias | derivadas
fecha: 2024-XX-XX
autor:
resumen: Una o dos frases. Aparece en portada, archivo y OG.
etiquetas: [lista]
carta: opcional, una línea editorial al inicio del artículo
---
```

SEO básico:

- `<title>` por página
- Open Graph + Twitter Cards vía Jekyll SEO Tag (o include manual)
- `sitemap.xml` vía jekyll-sitemap
- RSS vía jekyll-feed con un template custom para incluir sólo contenido
  público
- `robots.txt`
- `favicon.svg` mínimo (un cuadrado con la `i` de intersticio)

---

## 8. Deploy

- GitHub Pages con build via GitHub Actions
- Ruby 3.x + Jekyll 4.x
- Sin plugins de pago, sólo los soportados oficialmente en Pages más los
  whitelisted (`jekyll-feed`, `jekyll-sitemap`, `jekyll-seo-tag`,
  `jekyll-paginate`)
- Build automático en push a `main`
- URL resultante: `https://<usuario>.github.io/intersticio/` o dominio propio
  configurable vía `CNAME`

---

## 9. Criterios de éxito

1. Una persona que entra por primera vez entiende en menos de 5 segundos que
   es una publicación cultural, no un blog.
2. Un artículo se lee sin distracciones en cualquier viewport razonable.
3. La portada se siente como entrar a una sala de lectura, no a un feed.
4. El RSS contiene la pieza completa, no sólo excerpts.
5. El sitio se construye en menos de 30 segundos localmente.
6. Cero dependencias JS en producción.
7. Lighthouse accesibilidad ≥ 95.
