# PinoWeb · Plantillas web para negocios locales

Sistema de páginas web prediseñadas para ofrecer a negocios locales (peluquerías,
restaurantes, tiendas, clínicas, etc). Optimizadas para móvil, con reserva
online integrada y listas para mostrar en persona como demo.

## Estructura

```
index.html                       Landing principal · catálogo de plantillas
templates/
├── peluqueria/index.html        Demo · peluquería con reserva de cita
├── restaurante/index.html       Demo · restaurante con reserva de mesa
├── tienda/index.html            Demo · tienda con catálogo + reserva por WhatsApp
└── servicios/index.html         Demo · servicios (clínicas, fisios, talleres, etc.)
```

Cada plantilla es **un único archivo HTML autocontenido** (HTML + CSS + JS).
Eso significa: para hacer la web de un negocio nuevo, **solo tienes que editar
un archivo**.

## Flujo: crear una web para un negocio nuevo

1. **Copia la carpeta de la plantilla que mejor encaje**:
   ```bash
   cp -r templates/peluqueria templates/peluqueria-cliente-x
   ```

2. **Abre `index.html` de esa carpeta** y busca el bloque al inicio:
   ```js
   const CONFIG = { ... }
   ```

3. **Edita los datos del negocio**: nombre, teléfono, dirección, horario,
   servicios, fotos. Todo está comentado en español.

4. **Foto principal del hero**: sube una foto a Google (o usa la del perfil de
   Google Maps del negocio) y pega la URL en `CONFIG.fotoHero`. Puedes copiar
   la URL haciendo click derecho sobre la foto en Google Maps → "Copiar URL".

5. **Mapa de Google**: en Google Maps, busca el negocio → Compartir →
   "Insertar mapa" → copia el `src` del iframe y pégalo en `CONFIG.mapaEmbed`.

6. **WhatsApp**: en `CONFIG.whatsapp`, pon el número sin `+` ni espacios.
   Ej: `34612345678`.

7. **Listo**. Abre el archivo en el navegador del móvil para enseñarlo en
   persona.

## Plantillas

| Tipo de negocio | Plantilla | Características destacadas |
|---|---|---|
| Peluquería, barbería, estética | `peluqueria/` | Reserva de cita por servicio, equipo, galería, reseñas |
| Restaurante, bar, cafetería | `restaurante/` | Carta por categorías, reserva de mesa (comida/cena), galería |
| Tienda, boutique, retail | `tienda/` | Catálogo de productos, reserva en tienda por WhatsApp |
| Clínica, fisio, gym, taller, abogado, etc. | `servicios/` | Lista de servicios con precios, equipo, proceso, FAQs, reserva |

## Sistema de reservas

Las plantillas con reserva (peluquería, restaurante, servicios) tienen:

- **Calendario dinámico**: genera slots automáticamente según el horario del
  negocio configurado en `CONFIG.horario`.
- **Filtra horas pasadas y ocupadas**: las reservas existentes bloquean los
  huecos automáticamente.
- **Persistencia local (demo)**: guarda las reservas en `localStorage` para
  que la demo funcione visualmente sin servidor.
- **Notificación al negocio por WhatsApp**: cuando un cliente termina la
  reserva, se le ofrece un botón "Avisar al [negocio]" que abre WhatsApp con
  todos los datos prerellenados al teléfono del dueño.

### Pasar a producción (cliente con suscripción)

Cuando un negocio firme suscripción y quieras que las reservas se guarden de
forma real (no solo en `localStorage`), edita la función `guardarReserva()`
al final del `<script>` de cada plantilla. Hay un comentario:

```js
// TODO PRODUCCIÓN: enviar 'r' al backend (Supabase, Firebase, etc.)
// Ejemplo Supabase:
// await supabase.from('reservas').insert(r);
```

Opciones recomendadas (gratis hasta volumen alto):

- **Supabase** (Postgres + dashboard): https://supabase.com
- **Firebase Firestore**: https://firebase.google.com
- **Formspree** (más simple, solo emails): https://formspree.io

## Despliegue rápido

### Opción 1: GitHub Pages (gratis)
1. Push del repo a GitHub.
2. Settings → Pages → Source: `main` branch.
3. URL pública lista en `https://[usuario].github.io/[repo]/templates/peluqueria-cliente-x/`.

### Opción 2: Netlify Drop (más rápido para demos)
1. Ve a https://app.netlify.com/drop
2. Arrastra la carpeta del cliente.
3. Te da una URL pública en 5 segundos.

### Opción 3: Vercel
1. `npx vercel` desde la carpeta del cliente.
2. Web pública con dominio `[nombre].vercel.app`.

## Personalización visual

Cada plantilla tiene en su `CONFIG`:

```js
colorAccent: "#c9a961",    // Color principal (botones, acentos)
colorAccent2: "#e6c878",   // Color secundario (gradientes, hover)
```

Cambia estos dos valores y se aplican a toda la web automáticamente.

## Checklist rápido para cada nueva web

- [ ] Copiar plantilla a nueva carpeta con nombre del negocio
- [ ] Cambiar `nombre`, `subtitulo`, `eslogan`, `descripcion`
- [ ] Cambiar `telefono`, `whatsapp`, `email`, `direccion`
- [ ] Cambiar `mapaEmbed` con iframe de Google Maps del negocio real
- [ ] Cambiar `horario` con los horarios reales
- [ ] Cambiar `servicios` / `categorias` / `productos` (según plantilla)
- [ ] Cambiar `fotoHero` y galería con fotos reales (Google Maps, Instagram)
- [ ] Cambiar `colorAccent` para que combine con la marca del negocio
- [ ] Probar en el móvil antes de enseñarlo
- [ ] Hacer la reserva de prueba para verificar que el WhatsApp llega bien
