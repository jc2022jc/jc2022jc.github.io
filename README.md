# Aura Refugio · Departamento en alquiler en Huamanga

Página web de una sola pantalla (landing page) para promocionar el alquiler de un departamento amoblado en **Jr. Carlos F. Vivanco 474, Huamanga, Ayacucho**, antes del óvalo de Puente Nuevo.

El sitio está contenido en **un único archivo HTML autosuficiente**: estilos, scripts e imágenes van incrustados, por lo que funciona sin servidor ni carpetas adicionales.

---

## Archivo

| Archivo | Tamaño aprox. | Descripción |
|---|---|---|
| `Aura_Refugio___Alquiler_en_Huamanga__1_.html` | ~1.6 MB | Sitio completo (HTML + CSS + JS + 16 imágenes en base64) |

La única dependencia externa son las fuentes de Google Fonts (**Spectral** y **Karla**). Si no hay conexión, el sitio usa fuentes del sistema (Georgia / Segoe UI) sin romperse.

---

## Secciones del sitio

1. **Cabecera fija**: logotipo en forma de arco y menú (El departamento, Fotos, Ubicación, Consultar). En móvil solo queda visible el botón "Consultar".
2. **Portada**: indicador "Disponible para alquiler", título, texto de presentación, foto principal recortada en arco, medallón circular con la cocina y un sello giratorio "HUAMANGA ✦ AYACUCHO ✦ PERÚ".
3. **Datos rápidos**: Amoblado · 2 dormitorios · Cocina equipada · Mucha luz natural.
4. **Ambientes** (`#ambientes`): tres bloques alternados con fotos y características:
   - Sala y comedor
   - Cocina
   - Dormitorios, baño y zona de estudio
5. **Galería** (`#fotos`): 8 fotos en mosaico con visor ampliado.
6. **Huamanga**: bloque descriptivo sobre la ciudad y la zona.
7. **Cómo alquilar** (`#pasos`): Escríbenos → Visítalo → Múdate.
8. **Ubicación** (`#ubicacion`): dirección, referencia y botones a Google Maps ("Ver en Google Maps" y "Cómo llegar").
9. **Contacto** (`#contacto`): botones de WhatsApp y llamada.
10. **Pie de página** y **botón flotante de WhatsApp**.

---

## Funcionalidades

- **Contacto por WhatsApp y teléfono** generado automáticamente desde una constante (ver *Configuración*).
- **Visor de fotos**: se abre al tocar cualquier imagen de la galería; permite navegar con flechas en pantalla, teclado (← → y Esc) y deslizamiento táctil, y muestra la leyenda con el contador "n de 8".
- **Animaciones**: entrada escalonada de la portada y aparición suave de secciones al hacer scroll (`IntersectionObserver`). Se desactivan si el usuario tiene activado "reducir movimiento".
- **Botón flotante de WhatsApp**: aparece tras bajar unos 500 px y se oculta cuando la sección de contacto está en pantalla.
- **Modo claro / oscuro** automático según la preferencia del sistema.
- **Diseño responsive**: adaptado a escritorio, tablet y móvil (cortes en 860 px, 760 px y 600 px), incluidas las zonas seguras de iPhone (`safe-area-inset`).
- **Accesibilidad**: textos alternativos en todas las fotos, etiquetas `aria`, foco visible y retorno del foco al cerrar el visor.

---

## Configuración

### Número de contacto y mensaje de WhatsApp

Al final del archivo, dentro del bloque `<script>`:

```js
const TELEFONO = "51989913620";   // 51 (Perú) + celular, sin espacios ni "+"
const MENSAJE  = "Hola, vi la página de Aura Refugio y quisiera información sobre el departamento en Jr. Carlos F. Vivanco 474, Huamanga.";
```

Con estos dos valores se arman los enlaces del botón de WhatsApp, del botón flotante y del botón "Llamar".

### Colores

Definidos como variables al inicio del `<style>`, en `:root`:

| Variable | Uso | Claro | Oscuro |
|---|---|---|---|
| `--cal` | Fondo general | `#FBFAF7` | `#16191D` |
| `--piedra` | Fondos de banda | `#ECE6DB` | `#22262B` |
| `--madera` | Acentos (íconos, títulos) | `#6B3E1F` | `#D29A6C` |
| `--cielo` | Botones y sección de contacto | `#2D68AE` | `#7FB0EA` |
| `--cielo-hondo` | Sección Huamanga | `#1D4C86` | `#24476F` |
| `--tinta` | Texto principal | `#1E2833` | `#ECE8E1` |

Para cambiar la paleta, edita los valores en los tres bloques: `:root`, `@media (prefers-color-scheme: dark)` y `:root[data-theme="dark"]`.

### Textos, dirección y enlaces de mapa

Todo el contenido está en español directamente en el HTML. Si cambia la dirección, actualízala en:

- la etiqueta `<meta name="description">`
- la portada (texto de introducción)
- la sección `#ubicacion` (dirección y los dos enlaces de Google Maps)
- el pie de página
- la constante `MENSAJE` del script

### Imágenes

Las 16 imágenes están incrustadas como `data:image/...;base64`. Para reemplazar una foto:

1. Ubica la etiqueta `<img>` por su texto `alt` (por ejemplo, `alt="Baño con mayólicas azules"`).
2. Sustituye el valor de `src` por otra imagen en base64 o por una ruta a un archivo (`src="fotos/bano.jpg"`). Si usas rutas, distribuye la carpeta de fotos junto con el HTML.

La galería tiene 8 fotos con posiciones de mosaico `g1` a `g8`; si agregas o quitas fotos, ajusta también esas clases en el CSS.

---

## Cómo usarlo

- **Ver localmente**: abre el archivo `.html` con doble clic en cualquier navegador moderno.
- **Publicar**: súbelo tal cual a cualquier hosting estático (GitHub Pages, Netlify, Vercel, un hosting compartido, etc.). Conviene renombrarlo a `index.html`.
- **Compartir**: al ser un único archivo, también puede enviarse directamente por correo o mensajería.

---

## Tecnologías

HTML5 · CSS3 (Grid, Flexbox, `clamp()`, `color-mix()`, variables CSS, animaciones) · JavaScript sin librerías · Google Fonts.

Compatible con las versiones actuales de Chrome, Edge, Firefox y Safari (escritorio y móvil). `color-mix()` requiere navegadores de 2023 en adelante; en versiones más antiguas la cabecera translúcida puede verse sin transparencia.
