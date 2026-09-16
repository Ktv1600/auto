# 🔧 AutoPrecision — Landing Page Servicio Técnico Automotriz

Página web de presentación moderna, profesional y 100% responsiva para un taller de **servicio técnico automotriz**. Diseñada con enfoque mobile-first, paleta de colores original y microinteracciones sutiles.

---

## 📋 Tabla de contenidos

- [Vista previa](#vista-previa)
- [Stack tecnológico](#stack-tecnológico)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Secciones de la página](#secciones-de-la-página)
- [Paleta de colores](#paleta-de-colores)
- [Funcionalidades JavaScript](#funcionalidades-javascript)
- [Personalización](#personalización)
- [Despliegue](#despliegue)
- [Producción (Tailwind CLI)](#producción-tailwind-cli)

---

## Vista previa

| Dispositivo | Descripción |
|---|---|
| 🖥️ Desktop | Hero con anillo decorativo giratorio, grid de 3 columnas en servicios, layout de 2 columnas en contacto |
| 📱 Mobile | Menú hamburguesa, tarjetas en columna única, FAB WhatsApp siempre visible |
| 📟 Tablet | Layout intermedio, grid de 2 columnas en servicios y pilares |

---

## Stack tecnológico

| Tecnología | Versión / Fuente | Uso |
|---|---|---|
| **HTML5** | Semántico | Estructura base |
| **Tailwind CSS** | CDN Play (demo) | Estilos utilitarios + config personalizada |
| **JavaScript** | ES2015+ Vanilla | Toda la interactividad |
| **Google Fonts** | Inter + Poppins | Tipografía |
| **SVG inline** | Manual | Íconos y logo |

> ⚠️ El CDN de Tailwind (`cdn.tailwindcss.com`) es ideal para desarrollo y demos. Para producción, usar Tailwind CLI (ver sección abajo).

---

## Estructura del proyecto

```
auto/
├── index.html       ← Página principal (todo en un solo archivo)
└── README.md        ← Este archivo
```

El proyecto es intencionalmente un **single-file** para máxima portabilidad. Para escalar, se recomienda separar en:

```
auto/
├── index.html
├── css/
│   └── styles.css       ← Output de Tailwind CLI
├── js/
│   └── main.js          ← JavaScript extraído
└── assets/
    └── images/
```

---

## Secciones de la página

### 1. 🔝 Navbar / Header
- Fijo (`position: fixed`) con efecto **glassmorphism** (`backdrop-filter: blur`)
- Logo conceptual SVG: engranaje + rayo (cian + ámbar)
- Links de navegación con scroll suave a secciones
- Badge "Abierto ahora" con punto de pulso animado (verde)
- Botón CTA directo → sección Contacto
- **Menú hamburguesa** para mobile con transición `max-height`
- Sombra progresiva al hacer scroll (`IntersectionObserver`)

### 2. 🦸 Hero Section
- Fondo: grid de líneas + resplandores radiales (cian y ámbar)
- **Anillo giratorio** decorativo (solo escritorio ≥ 1280px)
- Badge de estado con punto pulsante
- Headline con gradiente texto `cian → blanco`
- Subtítulo descriptivo con énfasis
- 2 CTAs: primario (filled cyan) + secundario (outline)
- Stats: `+12 años`, `+5.000 vehículos`, `100% garantía`
- Flecha scroll-down animada (float)

### 3. 🛠️ Servicios destacados
6 tarjetas en cuadrícula (1 → 2 → 3 columnas según breakpoint):

| # | Servicio | Acento |
|---|---|---|
| 1 | Mecánica General | Cian |
| 2 | Scanner / Diagnóstico Electrónico | Ámbar |
| 3 | Mantenciones Preventivas | Cian |
| 4 | Frenos y Suspensión | Ámbar |
| 5 | Climatización A/C | Cian |
| 6 | Eléctrico Automotriz | Ámbar |

Efecto hover: `translateY(-6px)` + `box-shadow` cian + borde iluminado.

### 4. ✅ ¿Por qué elegirnos?
4 pilares de confianza:
- 🛡️ **Garantía escrita** — respaldo documental en cada reparación
- 📦 **Repuestos de calidad** — piezas originales o primera línea
- ⏱️ **Entrega en tiempo** — plazos honestos y cumplidos
- 🎓 **Técnicos certificados** — formación continua

Banner inferior con estrella y estadística de clientes.

### 5. 📩 Formulario de Contacto
Campos con validación cliente:

| Campo | Tipo | Validación |
|---|---|---|
| Nombre completo | `text` | Requerido |
| Teléfono | `tel` | Requerido + regex `[\d\s\+\-\(\)]{7,20}` |
| Correo electrónico | `email` | Requerido + regex email |
| Modelo/Año del vehículo | `text` | Requerido |
| Motivo de consulta | `textarea` | Requerido |

- Validación en `blur` + limpieza en tiempo real mientras escribe
- Toast de confirmación verde animado al enviar exitosamente
- Pendiente de conectar con backend / servicio de email (ver Personalización)

### 6. 💬 WhatsApp FAB
- Botón flotante fijo `bottom-6 right-6` (`z-index: 50`)
- Color oficial WhatsApp `#25D366`
- Mensaje precargado: *"Hola, quiero consultar por un servicio para mi vehículo"*
- Tooltip en hover (desktop)
- Efecto `scale(1.1)` + sombra verde al hover

### 7. 🦶 Footer
- Logo + descripción breve
- Links rápidos a servicios
- Horarios de atención con indicador "Abierto ahora"
- Datos de contacto (teléfono, email, dirección)
- Copyright + links legales

---

## Paleta de colores

Paleta diseñada desde cero para transmitir **tecnología automotriz, confianza y precisión**:

| Token | Hex | Rol |
|---|---|---|
| `void` | `#0A0C12` | Fondo principal (máximo oscuro) |
| `surface` | `#12151F` | Navbar, cards, formulario |
| `panel` | `#1C2033` | Tarjetas elevadas, pilares |
| `steel` | `#8B95A8` | Texto secundario, placeholders |
| `chrome` | `#C8D0DC` | Texto primario claro |
| `snow` | `#EEF1F6` | Títulos, texto blanco suave |
| `cyan` | `#00D4FF` | Acento tecnológico principal |
| `amber` | `#F5A623` | Acento cobrizo secundario |
| `edge` | `#252A3B` | Bordes, separadores, líneas |

### Gradientes especiales
```css
/* Texto gradiente principal (headlines) */
background: linear-gradient(135deg, #00D4FF 0%, #EEF1F6 60%);

/* Texto gradiente ámbar */
background: linear-gradient(135deg, #F5A623 0%, #EEF1F6 70%);

/* Separador decorativo */
background: linear-gradient(90deg, transparent, #00D4FF, transparent);
```

---

## Funcionalidades JavaScript

Todo vanilla JS, sin dependencias externas:

```
1. Navbar shadow         → scroll event listener (passive)
2. Mobile menu toggle    → classList.toggle('open') + aria-expanded
3. Reveal on scroll      → IntersectionObserver (threshold: 0.12)
4. Validación formulario → blur + input listeners, regex email/tel
5. Toast confirmación    → classList.add('show') + setTimeout
6. WhatsApp tooltip      → mouseenter/mouseleave opacity transition
```

---

## Personalización

### Cambiar número de WhatsApp
En `index.html`, buscar todas las ocurrencias de `56912345678` y reemplazar con el número real (formato internacional sin `+` ni espacios):

```html
<!-- Buscar y reemplazar: -->
href="https://wa.me/56912345678?text=..."
href="tel:+56912345678"
```

### Cambiar mensaje precargado de WhatsApp
Editar el parámetro `text=` en la URL (debe estar codificado en URL):

```
https://wa.me/NUMERO?text=Hola%2C+quiero+consultar+por+un+servicio
```

### Cambiar datos de contacto
Buscar y reemplazar en `index.html`:
- `contacto@autoprecision.cl` → tu correo real
- `Av. Los Mecánicos 1420, Local 5` → tu dirección real
- `+56 9 1234 5678` → tu teléfono real
- Horarios en la sección Footer → tus horarios reales

### Conectar el formulario a un backend
El formulario actualmente simula el envío. Para conectarlo:

**Opción A — FormSubmit (sin backend):**
```html
<form action="https://formsubmit.co/tu@email.com" method="POST">
  <input type="hidden" name="_subject" value="Nueva consulta AutoPrecision">
  <input type="hidden" name="_captcha" value="false">
  <!-- ... campos ... -->
</form>
```

**Opción B — Fetch API a tu endpoint:**
```javascript
form.addEventListener('submit', async (e) => {
  e.preventDefault();
  const data = Object.fromEntries(new FormData(form));
  const res = await fetch('/api/contact', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(data),
  });
  if (res.ok) showToast();
});
```

---

## Despliegue

El archivo `index.html` es completamente autónomo. Opciones de deploy:

| Plataforma | Pasos |
|---|---|
| **GitHub Pages** | Subir repo → Settings → Pages → Branch `main` / `root` |
| **Netlify** | Arrastrar carpeta `auto/` al dashboard de Netlify |
| **Vercel** | `vercel --prod` desde la carpeta del proyecto |
| **Hosting tradicional** | Subir `index.html` vía FTP a `public_html/` |

---

## Producción (Tailwind CLI)

Para optimizar el CSS y eliminar el CDN de desarrollo:

```bash
# 1. Instalar dependencias
npm init -y
npm install -D tailwindcss

# 2. Inicializar configuración
npx tailwindcss init

# 3. Crear archivo CSS de entrada
echo '@tailwind base; @tailwind components; @tailwind utilities;' > input.css

# 4. Compilar (minificado)
npx tailwindcss -i ./input.css -o ./css/styles.css --minify

# 5. En index.html, reemplazar el script CDN por:
# <link rel="stylesheet" href="./css/styles.css">
```

> 💡 Asegúrate de mover la configuración del objeto `tailwind.config` del `<script>` al archivo `tailwind.config.js` antes de compilar.

---

## Licencia

Proyecto de uso libre para fines comerciales y personales.  
Diseñado y desarrollado con **AutoPrecision** como nombre de marca de ejemplo — reemplazar con el nombre real del taller.

---

*Última actualización: Septiembre 2026*
