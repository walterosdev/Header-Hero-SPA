# GlowQueen — Spa & Beauty Hero

Landing page (sección *hero*) para **GlowQueen**, un spa de belleza y cuidado de la piel. Es una maquetación de un diseño de Figma hecha con **HTML + Tailwind CSS v4** y servida con **Vite**.

---

## 🚀 Cómo visualizarla

### Requisitos
- [Node.js](https://nodejs.org/) 20 o superior
- npm

### Instalación y ejecución

```bash
# 1. Instalar dependencias
npm install

# 2. Servidor de desarrollo (con recarga automática)
npm run dev
```

Abre en el navegador la URL que muestra la terminal (por defecto http://localhost:5173).

### Build de producción

```bash
npm run build     # genera la carpeta dist/
npm run preview   # sirve dist/ para comprobar el resultado final
```

> [!IMPORTANT]
> El diseño está pensado para **escritorio (aprox. 1440 px o más de ancho)**. La mayoría de elementos usan posicionamiento absoluto y el `body` tiene `overflow-hidden`, así que en pantallas pequeñas los elementos se pueden solapar o cortar. Todavía **no es responsive**.

---

## 🧱 Tecnologías

| Herramienta | Uso |
| --- | --- |
| [Vite](https://vite.dev/) | Servidor de desarrollo y empaquetado |
| [Tailwind CSS v4](https://tailwindcss.com/) | Estilos mediante clases utilitarias (plugin `@tailwindcss/vite`) |
| [Google Fonts – Poppins](https://fonts.google.com/specimen/Poppins) | Tipografía principal (pesos 300–700) |
| SVG | Logo, iconos e imágenes de fondo |

---

## 📁 Estructura del proyecto

```
spa-beauty-hero/
├── index.html          # Toda la maquetación de la página
├── vite.config.ts      # Configuración de Vite + plugin de Tailwind
├── package.json
├── public/             # Archivos estáticos copiados tal cual (favicon)
│   ├── favicon.svg
│   └── icons.svg
└── src/
    ├── style.css       # Import de Tailwind y paleta de colores (@theme)
    └── assets/         # Imágenes e iconos SVG
        ├── GlowQueen.svg          # Logo
        ├── chevron-down.svg       # Flecha del menú "More"
        ├── Search.svg             # Icono de búsqueda
        ├── Shopping Bag.svg       # Icono de carrito
        ├── beauty-woman-...svg    # Foto principal de la mujer
        ├── Rectangle 2.svg        # Bloque decorativo de fondo (derecha)
        ├── spa.svg                # Imagen decorativa de fondo
        ├── icon.svg               # Botón de play "Watch Video"
        ├── icon1.svg / icon2.svg / icon3.svg   # Iconos de las estadísticas
        └── “.svg                  # Comillas de los testimonios
```

---

## 🎨 Paleta de colores

Definida en [`src/style.css`](src/style.css) con la directiva `@theme` de Tailwind v4. Cada color se usa como clase (`bg-primary`, `text-muted`, etc.):

| Token | Hex | Uso |
| --- | --- | --- |
| `primary` | `#264065` | Títulos, enlaces, botones |
| `secondary` | `#A9D6CB` | Acento verde menta (logo, círculos de iconos) |
| `cream` | `#FAF8F5` | Fondo general de la página |
| `muted` | `#909090` | Textos secundarios |
| `canvas` | `#F5F5F5` | Fondo neutro alternativo |

---

## 🧩 Elementos de la página

La página está organizada en capas: unas imágenes decorativas al fondo (`-z-10`, `-z-20`) y el contenido por encima (`z-10` a `z-30`).

### 1. Header / barra de navegación
`<header>` en flex horizontal con:
- **Logo** `GlowQueen.svg`.
- **Menú principal**: *Home*, *About*, *Services*, *Facilities* y *More* (con flecha `chevron-down`).
- **Iconos** de búsqueda y carrito de compras.
- **Acceso de usuario**: enlace *Sign in* subrayado y botón redondeado *Sign up* (`bg-primary`).

### 2. Imágenes de fondo
Posicionadas en absoluto detrás del contenido y con `pointer-events-none` para que no bloqueen los clics:
- **Foto principal** de la mujer (`beauty-woman-...svg`), ocupa toda la altura de la pantalla.
- **`Rectangle 2.svg`** y **`spa.svg`**: formas decorativas a la derecha.
- Una **franja blanca** (`div` con `bg-white`) en la parte inferior, que sirve de base a las tarjetas.

### 3. Sección hero (texto principal)
`<main>` → `<section>` en columna (`flex-col`):
- **Título `h1`**: *"Bring back the beauty and glow of your skin"* (60 px, negrita, `text-primary`).
- **Párrafo** descriptivo en `text-muted`.
- **Acciones** en una fila `flex items-center`:
  - Botón **Book Now** (píldora azul, `rounded-full`).
  - Enlace **Watch Video**: icono de play `icon.svg` (48×48, `rounded-full shadow-xl`) + texto.

> [!NOTE]
> El icono `icon.svg` está recortado a 48×48 (`viewBox="50 26 48 48"`) y sin la sombra que exporta Figma. La sombra la pone Tailwind (`shadow-xl`); así el icono se alinea bien con el botón y no aparece un recuadro alrededor.

### 4. Tarjeta de estadísticas
Tarjeta blanca (`bg-white rounded-2xl`) con tres columnas distribuidas con `justify-evenly`:

| Icono | Cifra | Texto |
| --- | --- | --- |
| `icon1.svg` | **15+** | Special Treatments |
| `icon2.svg` | **25+** | Profesional Therapist |
| `icon3.svg` | **100%** | Herbal Cream Formula |

### 5. Testimonios
Columna a la derecha, sobre la foto, con dos tarjetas semitransparentes (`bg-white/30 rounded-2xl`), una desplazada respecto a la otra:
- **Sophia Princeton** — cliente habitual de los tratamientos.
- **Tamara Jules** — encontró en GlowQueen la solución para su piel complicada.

Cada tarjeta tiene el icono de comillas (`“.svg`), el texto del testimonio y el nombre en negrita.

---

## 📝 Notas y mejoras pendientes

- [ ] Hacer el diseño **responsive** (usar flex/grid y breakpoints `md:`, `lg:` en lugar de posiciones absolutas).
- [ ] Usar rutas de imágenes consistentes: ahora se mezclan `src/assets/...` y `/src/assets/...`. Conviene revisar que todas aparezcan en `dist/` después de `npm run build`.
- [ ] Evitar espacios y caracteres especiales en los nombres de archivo (`Shopping Bag.svg`, `Rectangle 2.svg`, `“.svg`). Por ejemplo: `shopping-bag.svg`, `quote.svg`.
- [ ] No anidar `<a>` dentro de `<button>` (*Sign up*, *Book Now*): usar solo un `<a>` con estilos de botón.
- [ ] Añadir textos `alt` descriptivos (ahora varios iconos usan `alt="icon1"`).
- [ ] Cambiar el `<title>` por algo como *"GlowQueen — Spa & Beauty"*.

