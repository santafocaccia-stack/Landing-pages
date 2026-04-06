# CLAUDE.md — Proyecto Atmosféricos Sur

## Qué es este proyecto

Landing page de **Atmosféricos Sur**, un servicio de camión atmosférico con 45 años de experiencia en **José C. Paz, Buenos Aires, Argentina**. El objetivo de la página es convertir visitantes en contactos por WhatsApp.

## Arquitectura

- Archivo principal: `index.html` (todo-en-uno: HTML + CSS inline + JS inline)
- Hosting: Netlify (deploy automático desde GitHub)
- Dominio: https://atmosfericos-sur.netlify.app
- Repo: GitHub → push a main = deploy automático
- No hay build step, framework, ni dependencias — es HTML estático puro

## Stack técnico

- HTML5 semántico
- CSS puro con custom properties (variables)
- JavaScript vanilla (sin librerías)
- Google Fonts: Oswald (títulos) + DM Sans (cuerpo)
- Google Analytics GA4: ID `G-Y3YMGWFFM8`

## Paleta de colores

```
--black: #080909        (fondo hero)
--dark: #0e1012         (fondo principal)
--card: #14171b         (fondo tarjetas)
--card2: #1a1e24        (fondo headers de tarjetas)
--border: #272c35       (bordes sutiles)
--border2: #323840      (bordes interactivos)
--accent: #f0b429       (amarillo principal — CTA, acentos)
--accent-dim: #b8871e   (amarillo oscuro — hover)
--accent-glow: rgba(240,180,41,0.18)
--text: #dde1ea         (texto principal)
--muted: #6b7385        (texto secundario)
--white: #ffffff
--green: #27c475        (estados completados, éxito)
--wa-green: #25d366     (botón WhatsApp)
```

## Tipografía

- **Títulos**: Oswald, weight 600-700, uppercase, line-height 0.9
- **Cuerpo**: DM Sans, weight 400-500, 15-17px, line-height 1.55-1.65
- **Labels pequeños**: Oswald, 10-11px, letter-spacing 0.14-0.22em, uppercase
- Hero H1: `clamp(56px, 13vw, 92px)`

## Estética y dirección visual

- Tema OSCURO industrial/urgente (apropiado para servicio local de emergencia)
- Textura de ruido SVG en fondo fijo (noise overlay)
- Grilla de puntos sutiles en fondo
- Diagonal clip-path entre hero y contenido
- Emoji decorativo 🚛 grande semitransparente en hero (opacity 0.05)
- Borde izquierdo amarillo en opciones seleccionadas (scaleY animado)
- Botón CTA con glow en hover
- Animaciones: fadeUp, fadeDown, slideUp, pulse (todo CSS puro)

## Estructura de la página

1. **Hero** — Badge "Servicio en José C. Paz" + H1 "Atmosféricos Sur" + subtítulo + descripción
2. **Trust strip** — 4 señales: Mismo día / 45 años / José C. Paz / Sin compromiso
3. **Funnel de 3 pasos** (formulario multi-step):
   - Paso 1: ¿Qué necesitás resolver? (6 opciones: pozo lleno, desagote, cañería tapada, limpieza cámara, desagote cámara, no seguro)
   - Paso 2: ¿En qué barrio? (input texto con datalist de barrios)
   - Paso 3: ¿Para cuándo? (4 opciones de urgencia)
   - Pantalla de éxito con botón WhatsApp
4. **Reassurance** — "Sin turno previo. 45 años en José C. Paz"
5. **Footer** — Mínimo, solo nombre + ubicación
6. **Botón flotante WhatsApp** — Fijo abajo a la derecha, siempre visible

## Datos del negocio

- **Nombre**: Atmosféricos Sur
- **Teléfono WhatsApp**: 5491166192080
- **Ubicación**: José C. Paz, GBA (Gran Buenos Aires), Argentina
- **Antigüedad**: 45 años
- **Servicios**: Desagote de pozos, destapación de cañerías, limpieza de cámaras sépticas, desagote de cámaras
- **Barrios que cubre**: Sol y Verde, Barrio Sarmiento, Villa Altube, Centro, Villa del Parque, Los Aromos, San Jorge, Villa Lucia, El Triangulo

## Tracking y analytics

El sitio usa GA4 con eventos custom:
- `funnel_inicio` — cuando carga la página
- `funnel_paso` — cada cambio de paso (con parámetro `step`)
- `servicio_seleccionado` — cuando eligen un servicio
- `urgencia_seleccionada` — cuando eligen urgencia
- `whatsapp_click` — cuando llegan al final (con servicio, barrio, urgencia)

## WhatsApp

El mensaje se arma automáticamente con las respuestas del funnel:
```
Hola! Consulto por: [servicio].
Barrio: [barrio].
Cuando: [urgencia].
```
URL: `https://wa.me/5491166192080?text=[mensaje codificado]`

## Reglas para editar este proyecto

1. **Todo en un solo archivo** — No separar CSS ni JS en archivos externos (por ahora)
2. **Mobile-first** — El 83% del tráfico es celular. Tap targets mínimo 44px
3. **Sin frameworks** — No agregar React, Tailwind, Bootstrap ni nada. CSS y JS puros
4. **Mantener la estética oscura industrial** — No cambiar a temas claros
5. **Acento amarillo #f0b429** — Es el color de marca, no cambiar
6. **Idioma**: Todo en español argentino (vos, tenés, necesitás)
7. **Un solo CTA**: WhatsApp. No agregar formularios de email, teléfono ni redes sociales
8. **No agregar menú de navegación** — Es una landing, no un sitio web
9. **Accesibilidad**: Usar aria-labels, roles, focus-visible en elementos interactivos
10. **Performance**: No agregar librerías pesadas. Mantener el HTML liviano
11. **Al hacer commits**: Mensajes en español, descriptivos. Ejemplo: "Agrega botón flotante de WhatsApp"

## SEO

- Title: "Atmosféricos Sur – Camión Atmosférico en José C. Paz | Desagote y Destapaciones"
- Meta description incluida
- Open Graph y Twitter Card configurados
- Schema JSON-LD de LocalBusiness incluido
- Canonical URL: https://atmosfericos-sur.netlify.app/
- og:image apunta a og-image.png (pendiente de crear)

## Contexto del proyecto mayor: Faro Clientes

Este proyecto forma parte de **Faro Clientes**, una iniciativa para gestionar y optimizar la captación de clientes para negocios locales. Atmosféricos Sur es el primer caso de uso. Las lecciones y patrones que funcionan acá se van a replicar para otros negocios.
