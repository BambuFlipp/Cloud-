# Sergiu Obras y Reformas Vinaròs — Web informativa

Web estática informativa para la empresa de construcción y reformas
**Sergiu Obras y Reformas Vinaròs** (Av. de Maria Auxiliadora, 46 · 12500 Vinaròs, Castelló).

## Características

- Diseño moderno y elegante, mobile-first y completamente responsive.
- Animaciones de scroll suaves (IntersectionObserver) y micro-interacciones.
- Botón flotante de WhatsApp + CTAs "Solicitar presupuesto" en toda la página.
- Secciones: Hero, Servicios, Sobre nosotros / Proceso, Galería de proyectos, Contacto + mapa embebido de Google Maps.
- SEO básico (meta tags, Open Graph, JSON-LD `GeneralContractor`).
- Sin frameworks: HTML + CSS + JS plano. Funciona simplemente abriendo `index.html`.

## Estructura

```
index.html
assets/
  css/styles.css
  js/main.js
  img/favicon.svg
```

## Cómo personalizar

### 1. Número de WhatsApp

Configurado: **+34 624 896 471**. Si en el futuro cambia, basta con un
buscar/reemplazar de `34624896471` en `index.html`.

### 2. Fotos reales

Las imágenes de la galería son placeholders de Unsplash. Para usar las
fotos reales del negocio:

1. Coloca las fotos en `assets/img/` (ej. `proyecto-1.jpg`, `proyecto-2.jpg`...).
2. En `assets/css/styles.css`, sustituye las URLs de las clases
   `.gallery__img--1` a `.gallery__img--8` (y `.hero__bg-img`,
   `.about__media-main`, `.about__media-accent`) por las rutas locales.

### 3. Textos

Todos los textos están en `index.html`. Edítalos directamente: tagline del
hero, lista de servicios, pasos del proceso, dirección, horario, etc.

## Despliegue

Al ser una web estática se puede subir tal cual a:

- GitHub Pages (rama del repo + Pages activado).
- Netlify / Vercel (drag & drop de la carpeta).
- Cualquier hosting con FTP.
