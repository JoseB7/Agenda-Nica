# AgendaNica — Documentación del Proyecto

## ¿Qué es esto?
Frontend completo de una web editorial de ocio y cultura para Managua y Nicaragua.
Estilo: magazine de ciudad premium, urban lifestyle, inspirado en city guides editoriales.

---

## Estructura del archivo único `index.html`

```
index.html
├── <head>
│   ├── Google Fonts (Playfair Display, Cormorant Garamond, Libre Franklin)
│   └── <style> — todo el CSS (tokens, componentes, responsive)
│
├── <body>
│   ├── SEARCH OVERLAY       — modal de búsqueda a pantalla completa
│   ├── HEADER               — logo + nav desktop + búsqueda + menú móvil
│   ├── TICKER               — franja animada de noticias del día
│   ├── DATE STRIP           — franja de categorías y metadatos
│   ├── HERO                 — historia principal grande + 3 tarjetas laterales
│   ├── FEATURED STRIP       — top 3 recomendaciones numeradas
│   ├── RESTAURANTES         — grid editorial con 4 tipos de tarjetas
│   ├── NOTA EDITORIAL       — sección fondo teal con texto + mini-cards
│   ├── FIN DE SEMANA        — 4 tarjetas de actividades con numeración
│   ├── ESCAPADAS            — hero grande + grid 3 destinos
│   ├── CAFÉS                — grid oscuro 4 cafés con hover effects
│   ├── AGENDA CULTURAL      — lista de eventos + sidebar (populares, social, CTA)
│   ├── RINCONES FOTOGÉNICOS — masonry fotográfico con overlay en hover
│   ├── NEWSLETTER           — sección terracota con form y ventajas
│   ├── FOOTER               — 4 columnas + barra inferior
│   └── SCROLL TO TOP        — botón flotante
│
└── <script> — header scroll, menú móvil, overlay búsqueda, newsletter, IntersectionObserver
```

---

## Paleta de color (CSS variables)
| Variable        | Hex       | Uso                        |
|-----------------|-----------|----------------------------|
| `--ivory`       | #F5F1E8   | Fondo principal            |
| `--ivory-dark`  | #EDE8DC   | Fondos alternativos        |
| `--black`       | #1E1E1C   | Texto, fondos oscuros      |
| `--teal`        | #1F6D67   | Acento principal, CTAs     |
| `--terra`       | #B85C38   | Categorías, badges         |
| `--mustard`     | #C79A3B   | Eyebrows, destacados       |

---

## Tipografía
- **Playfair Display** — Títulos hero y sección (900/700)
- **Cormorant Garamond** — Títulos de tarjetas y cards (serif elegante)
- **Libre Franklin** — Cuerpo, labels, UI (sans-serif editorial)

---

## Cómo correrlo localmente

### Opción 1 — Abrir directamente
```bash
# Simplemente abre el archivo en tu navegador:
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

### Opción 2 — Servidor local (recomendado para desarrollo)
```bash
# Con Python (preinstalado en macOS/Linux):
python3 -m http.server 3000
# Visita: http://localhost:3000

# Con Node.js:
npx serve .
# Visita: http://localhost:3000

# Con VS Code:
# Instala la extensión "Live Server" y haz clic en "Go Live"
```

### Opción 3 — Subir a Netlify (gratis, 1 minuto)
1. Arrastra la carpeta `agendanica/` a https://app.netlify.com/drop
2. Obtén URL pública instantánea. Listo.

---

## Cómo convertir a Divi (WordPress)

### Paso 1 — Configura los colores globales en Divi
`Divi → Theme Customizer → General Settings → Layout`
Añade los colores de la paleta en "Custom CSS" del customizer:
```css
:root {
  --ivory: #F5F1E8;
  --teal: #1F6D67;
  --terra: #B85C38;
  --mustard: #C79A3B;
  --black: #1E1E1C;
}
```

### Paso 2 — Instala los fonts en Divi
`Divi → Theme Customizer → Typography`
- Heading Font: **Playfair Display**
- Body Font: **Libre Franklin**

Para Cormorant Garamond, añade en functions.php:
```php
function agendanica_fonts() {
  wp_enqueue_style('agendanica-fonts',
    'https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,600;1,400&display=swap');
}
add_action('wp_enqueue_scripts', 'agendanica_fonts');
```

### Paso 3 — Mapeo de secciones HTML → Módulos Divi

| Sección HTML         | Módulo Divi                              |
|----------------------|------------------------------------------|
| HEADER               | Divi Theme Header Builder (menú + logo)  |
| TICKER               | Marquee Slider (plugin) o Code Module    |
| HERO principal       | Fullwidth Header con imagen de fondo     |
| Hero cards laterales | Image con overlay + Text Module          |
| FEATURED STRIP       | Blurb Module (ícono numérico + texto)    |
| Cards de restaurantes| Blog Module (estilo grid) o Portfolio    |
| Nota Editorial       | Row de 2 columnas: Text + Blog           |
| FIN DE SEMANA        | Portfolio Module (4 columnas)            |
| ESCAPADAS hero       | Fullwidth Slider                         |
| Escapadas grid       | Portfolio (3 columnas) con overlay       |
| CAFÉS                | Portfolio Module (dark background)       |
| AGENDA CULTURAL      | Blog Module lista + Sidebar con widgets  |
| MASONRY FOTOS        | Gallery Module (masonry) o Filterable    |
| NEWSLETTER           | Email Optin Module con Custom CSS        |
| FOOTER               | Divi Footer Builder (4 columnas)         |

### Paso 4 — Crear las Custom Post Types
Instala el plugin **Custom Post Type UI** y crea:
- `restaurantes` (Restaurantes)
- `eventos` (Agenda)
- `escapadas` (Escapadas)
- `cafes` (Cafés)
- `rincones` (Fotogénico)

Asigna taxonomías: `barrio`, `categoria`, `precio`.

### Paso 5 — CSS personalizado en Divi
Pega el CSS de las variables y las tipografías en:
`Divi → Theme Options → Custom CSS`
Puedes reutilizar las clases `.eyebrow`, `.card`, `.label` del HTML directamente en módulos con Clase CSS adicional en Divi Builder.

### Paso 6 — El ticker
Para reproducir el ticker animado en Divi, usa un **Code Module** con el HTML del ticker y el CSS del bloque `/* ─── TICKER ─────── */`.

---

## Archivos opcionales para escalar

Si quieres convertirlo a Next.js + Tailwind más adelante:

```bash
npx create-next-app@latest agendanica --typescript --tailwind --app
```

La estructura de componentes sería:
```
components/
├── Header.tsx
├── Ticker.tsx
├── Hero.tsx
├── ArticleCard.tsx
├── EventItem.tsx
├── CafeCard.tsx
├── PhotoMasonry.tsx
├── Newsletter.tsx
└── Footer.tsx
```

---

## Notas de diseño

- Todas las animaciones de entrada usan `IntersectionObserver` nativo (sin dependencias)
- El CSS usa `clamp()` para tipografía fluida en todos los breakpoints
- Los breakpoints son: 1100px (tablet landscape), 900px (tablet), 640px (mobile)
- Las imágenes usan Unsplash con parámetros `?w=&q=80&auto=format` para optimización
- En producción, reemplaza las imágenes de Unsplash por imágenes propias o de Nicaragua
- El archivo es completamente autónomo — cero dependencias externas excepto Google Fonts

---

*AgendaNica — Managua, Nicaragua · 2025*
