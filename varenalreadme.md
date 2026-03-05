# VARENAL — Documentación del Proyecto

Documentación completa del tema Shopify personalizado para la marca VARENAL.  
Última actualización: 4 de marzo de 2026.

---

## 1. Visión General

| Campo | Detalle |
|---|---|
| **Marca** | VARENAL |
| **Producto principal** | Almohadilla de calor inalámbrica para tobillo (CL-2888) |
| **Modelo de negocio** | Dropshipping vía AutoDS desde AliExpress |
| **Tiempo de envío real** | ~14 días |
| **Idioma del tema** | Español (archivo locale: `es.default.json`) |
| **Mercado objetivo** | Latinoamérica (inicialmente Colombia) |
| **Estado** | Tema conectado a Shopify vía GitHub, publicado como tema de desarrollo |

### Propósito

Crear una tienda online de bienestar con un tema Shopify 2.0 completamente personalizado, optimizado para conversión, 100% en español, con diseño premium y animaciones modernas. El enfoque es un embudo de ventas de una sola página (landing page → producto → compra).

### Especificaciones del Producto CL-2888

- 3 niveles de calor: 48°C / 53°C / 58°C
- Vibración terapéutica
- Pantalla LED táctil
- Batería 2000mAh (inalámbrico, recargable)
- Apagado automático a los 15 minutos
- Forro de felpa suave
- Diseño universal (ambos tobillos)

---

## 2. Identidad Visual (Design System v3.0)

### Colores

| Token | Valor | Uso |
|---|---|---|
| `--color-primary` | `#00B4C8` | CTAs, enlaces, acentos |
| `--color-dark` | `#1A1A2E` | Fondos oscuros, texto principal |
| `--color-accent` | `#FF6B35` | Badges, urgencia, precios de descuento |
| `--color-text` | `#2D2D2D` | Texto body |
| `--color-text-muted` | `#6B7280` | Texto secundario |
| `--gradient-brand` | `#00B4C8 → #0090A0` | Gradiente de marca en botones y precios |

### Tipografía

| Rol | Fuente | Peso |
|---|---|---|
| Títulos | Montserrat | 700–800 |
| Cuerpo | Inter | 400–500 |
| Técnica/badges | Space Grotesk | 600 |

### Animaciones

El tema usa un sistema de animaciones rico basado en CSS:
- **Spring easing** (`cubic-bezier(0.34, 1.56, 0.64, 1)`) para hover y microinteracciones
- **morphBlob** — animación orgánica de formas de fondo
- **pulseGlow** — efecto de brillo pulsante en CTAs
- **shimmerSweep** — barrido de brillo en botones
- **fadeInUp / fadeInLeft / fadeInRight** — scroll animations con 5 tiempos de stagger
- **Glass-morphism** — efectos de vidrio esmerilado en cards
- `prefers-reduced-motion` respetado para accesibilidad

---

## 3. Infraestructura Técnica

### Plataformas y Repositorio

| Servicio | Detalle |
|---|---|
| **Shopify** | `ic11en-e6.myshopify.com` |
| **GitHub** | `https://github.com/Ppkeash/Varenalwebs` (rama `main`) |
| **Directorio local** | `C:\Users\yeval\...\varenal-theme\` |
| **Cuenta Shopify** | `valbuenaesteban19@gmail.com` |
| **Cuenta GitHub** | `Ppkeash` |

### Herramientas

| Herramienta | Versión |
|---|---|
| Node.js | v22.15.0 |
| Git | 2.49.0 |
| Shopify CLI | v3.91.0 |

### Conexión Shopify ↔ GitHub

El tema está conectado directamente desde Shopify Admin → Temas → "Conectar desde GitHub". Esto significa que:
- Los cambios pusheados a `main` se sincronizan automáticamente con Shopify
- Shopify también puede pushear cambios al repo (ediciones desde el theme editor)
- Esos pushes de Shopify pueden inyectar comentarios `/* ... */` en archivos JSON (inválidos) — se deben eliminar si aparecen

---

## 4. Estructura del Tema

```
varenal-theme/
├── assets/
│   ├── critical.css                  # Reset CSS, tipografía base, grid del layout
│   └── varenal-design-system.css     # Design system v3.0 completo (colores, botones, animaciones)
├── blocks/
│   ├── group.liquid                  # Wrapper flex horizontal/vertical para bloques anidados
│   └── text.liquid                   # Bloque de texto con estilos (título/subtítulo/normal)
├── config/
│   ├── settings_data.json            # Datos activos del tema (valores del theme editor)
│   └── settings_schema.json          # Esquema de personalización (fuentes, colores, logo)
├── layout/
│   ├── theme.liquid                  # Layout principal: head, fonts, CSS, body
│   └── password.liquid               # Layout de página de contraseña
├── locales/
│   ├── es.default.json               # Traducciones de la tienda (español)
│   └── es.default.schema.json        # Traducciones del editor del tema (español)
├── sections/
│   ├── header.liquid                 # Header sticky: logo, menú hamburguesa, carrito
│   ├── announcement-bar.liquid       # Barra de anuncio superior (envío gratis)
│   ├── footer.liquid                 # Footer 4 columnas + newsletter + iconos de pago
│   ├── header-group.json             # Grupo: announcement-bar → header
│   ├── footer-group.json             # Grupo: footer
│   ├── product.liquid                # Página de producto con galería, variantes, carrito
│   ├── collection.liquid             # Grid de colección con filtros y paginación
│   ├── cart.liquid                   # Página del carrito
│   ├── blog.liquid                   # Listado de artículos del blog
│   ├── article.liquid                # Página individual de artículo
│   ├── search.liquid                 # Página de búsqueda
│   ├── page.liquid                   # Páginas estáticas
│   ├── collections.liquid            # Lista de todas las colecciones
│   ├── 404.liquid                    # Página de error 404
│   └── password.liquid               # Página de contraseña de la tienda
├── snippets/
│   ├── css-variables.liquid          # Variables CSS dinámicas desde settings
│   ├── image.liquid                  # Componente de imagen responsive
│   └── meta-tags.liquid              # OpenGraph, Twitter Cards, structured data
├── templates/
│   ├── index.json                    # Homepage: embudo de 5 secciones VARENAL
│   ├── product.json                  # Plantilla de producto
│   ├── collection.json               # Plantilla de colección
│   ├── cart.json                     # Plantilla del carrito
│   ├── blog.json                     # Plantilla del blog
│   ├── article.json                  # Plantilla de artículo
│   ├── search.json                   # Plantilla de búsqueda
│   ├── page.json                     # Plantilla de páginas
│   ├── password.json                 # Plantilla de contraseña
│   ├── list-collections.json         # Plantilla de lista de colecciones
│   ├── 404.json                      # Plantilla de error 404
│   └── gift_card.liquid              # Tarjeta de regalo (standalone)
└── varenalreadme.md                  # Este archivo
```

---

## 5. Homepage — Embudo de Conversión

El homepage (`templates/index.json`) está diseñado como un embudo de ventas de una sola página con 5 secciones personalizadas:

### Flujo de secciones

| # | Sección | Tipo | Propósito |
|---|---|---|---|
| 1 | **VARENAL Hero** | `varenal-hero` | Impacto visual + CTA principal. Product picker conectado, badge, headline, prueba social, chips de specs, barra de confianza (3 items: envío gratis, garantía, certificación) |
| 2 | **Puntos de Dolor** | `varenal-pain-points` | Identificar el problema del usuario. 4 cards con emoji, título y cuerpo describiendo situaciones de dolor |
| 3 | **Características** | `varenal-features` | Mostrar la solución. 3 bloques con imagen, badge y texto descriptivo de las features del producto |
| 4 | **Reseñas** | `varenal-reviews` | Prueba social. 6 reseñas humanizadas con historias reales, barra de stats (4.8★, 2,300+ verificadas, 96% recomendación) |
| 5 | **CTA Final** | `varenal-final-cta` | Cierre de venta. Product picker, imagen, badges de confianza, CTA prominente |

### Las 6 Reseñas (humanizadas)

Las reseñas están escritas con lenguaje coloquial latinoamericano para generar autenticidad:

1. **Carolina R.** ★★★★★ — Enfermera 7 años, colega le mostró el producto, llora de alivio tras usar
2. **Andrés M.** ★★★★★ — Se lastimó el tobillo jugando basketball, el fisio le preguntó qué usaba
3. **María L.** ★★★★★ — Lo compró para gym, su mamá de 72 años se lo quitó para la artritis, tuvo que pedir otro
4. **Diego S.** ★★★★☆ — Honesto sobre el envío (~2 semanas), desea más colores, pero el producto cumple lo prometido
5. **Ana P.** ★★★★★ — Regalo para la abuela, la abuela llamó 3 días después agradecida
6. **Sebastián V.** ★★★★★ — CrossFit 5-6 veces/semana, la novia también lo usa

> **Nota estratégica:** La reseña de Diego (4★) maneja honestamente la expectativa de envío sin decir "14 días" explícitamente. Dice "tardó como 2 semanas".

---

## 6. Página de Producto

La sección `product.liquid` incluye:

- **Galería de imágenes** con thumbnails y cambio de imagen al seleccionar variante (con animación fade)
- **Selector de variantes** con dropdown que actualiza imagen, precio y botón dinámicamente
- **Precio dinámico** con compare_at_price, badge de "Ahorra X", precio tachado
- **Mini features** con íconos SVG: 3 niveles de calor, inalámbrico, LED táctil, apagado automático
- **Botón de agregar al carrito** con precio y estado dinámico (agotado/disponible)
- **Botón de pago rápido** de Shopify (`payment_button`)
- **Badges de confianza**: Envío Gratis, Garantía 60 Días, Pago Seguro
- **Responsive**: En mobile, la info va primero y la galería después
- **JavaScript**: Cambio de variante → actualiza imagen (con transición), precio, botón. Thumbnails clickeables.

---

## 7. Secciones Globales

### Header (`header.liquid`)
- Logo con enlace al inicio
- Navegación con menú configurable desde Shopify
- Menú hamburguesa en mobile con overlay
- Íconos de cuenta y carrito con counter dinámico
- Header sticky con sombra al scrollear
- Todos los aria-labels en español

### Footer (`footer.liquid`)
- 4 columnas: Marca (logo + descripción) / Enlaces rápidos / Soporte / Newsletter
- Formulario de suscripción a newsletter
- Línea de copyright
- Íconos de métodos de pago
- Todo en español

### Announcement Bar (`announcement-bar.liquid`)
- Barra superior con texto configurable
- Default: "Envío gratis en todos los pedidos"

---

## 8. Secciones Estándar

| Sección | Descripción |
|---|---|
| `collection.liquid` | Grid responsive de productos con filtrado y paginación |
| `cart.liquid` | Tabla de carrito con actualización de cantidades, nota del pedido, botón de checkout |
| `blog.liquid` | Grid de artículos con imagen, título, fecha, extracto |
| `article.liquid` | Artículo individual con imagen hero, contenido, compartir en redes, comentarios |
| `search.liquid` | Búsqueda con formulario y grid de resultados |
| `page.liquid` | Contenido de página estática |
| `collections.liquid` | Lista de todas las colecciones con imagen y título |
| `404.liquid` | Mensaje de error con CTA para volver al inicio |
| `password.liquid` | Página de contraseña para tiendas en desarrollo |

---

## 9. Sistema de Traducción

### Arquitectura

- Archivo de traducciones: `locales/es.default.json`
- Archivo de traducciones del editor: `locales/es.default.schema.json`
- **Todo el texto visible al usuario** usa filtro `{{ 'clave' | t }}`
- El archivo se llama `es.default` para que Shopify reconozca español como idioma base

### Cobertura de traducciones

Todas las áreas están traducidas al español:
- Secciones del homepage (hero, reseñas, features, etc.)
- Carrito, checkout prompt, formularios
- Blog, artículos, comentarios
- Búsqueda, colección, paginación
- Errores 404, contraseña
- Footer, header, meta tags
- Schema labels del editor del tema

### Nota sobre el checkout

El checkout de Shopify no se controla desde el tema. Para que el checkout esté en español:
1. Shopify Admin → Settings → Languages
2. Agregar Español como idioma principal
3. Esto traduce checkout, emails y notificaciones

---

## 10. Problemas Resueltos

### Fase 1-3: Setup inicial y primera versión
- **Error de sintaxis Liquid**: `{% if forloop.index0 | modulo: 2 == 1 %}` — se separó en assign + if
- **ERR_CONNECTION_REFUSED en `shopify theme dev`**: Conflicto con OneDrive/firewall. Solución: usar `shopify theme push` directamente
- **Tema roto "VARENAL"**: Push con `--unpublished` creó tema vacío. Se eliminó manualmente
- **Codificación PowerShell**: `Set-Content` corrompía emojis sin `-Encoding UTF8`

### Fase 4: Rediseño VARENAL + español
- Se crearon 5 secciones custom del embudo de conversión
- Se eliminaron 10 secciones genéricas no usadas (hello-world, hero-banner, cta-banner, testimonials, custom-section, faq-accordion, features-grid, how-it-works, product-showcase, trust-bar)
- Traducción completa al español

### Fase 5: Conexión producto → CTA
- Los botones CTA del hero y final-cta no enlazaban a nada (`#`)
- Se añadió product picker a ambas secciones
- Auto-detección del primer producto de la tienda como fallback

### Fase 6: Consistencia de diseño
- Todas las secciones de templates (cart, collection, blog, etc.) se rediseñaron con el design system VARENAL

### Fase 7: Mobile responsiveness
- Overhaul completo de responsive: hero, pain points, features, reviews, final CTA, header, product, cart, collection, blog, article, search

### Fase 8: Animaciones v3.0
- Spring easing, glass-morphism, SVG icons, gradient text, pulse rings, morphing blobs
- Design system CSS consolidado en `varenal-design-system.css`
- Nombres latinos en reseñas, limpieza de CSS duplicado

### Fase 9: Variant image switching
- Cambio de imagen al seleccionar variante (con animación fade)
- Thumbnails clickeables
- Precio dinámico con compare_at_price
- Se implementó → se revirtió → se restauró (por conflictos)

### Fase 10: Ajuste de envío, español completo, reseñas
- **Envío**: Se eliminó "Envío en 24h" (falso, el producto tarda ~14 días). Reemplazado por "Envío gratis"
- **Español**: Se encontraron y corrigieron restos en inglés en 11 archivos (aria-labels, defaults, alt text, schema labels, meta tags)
- **Reseñas**: Se reescribieron las 6 reseñas con historias personales creíbles y lenguaje coloquial latino

### Fase 11: Correcciones técnicas
- **Comentarios JSON inválidos**: Shopify inyectó bloques `/* ... */` en 15 archivos JSON al sincronizar. Se eliminaron todos
- **Idioma del tema**: Archivos de locale renombrados de `en.default.*` → `es.default.*` para que Shopify reconozca español como idioma base

---

## 11. Lo que NO tiene el tema

- **No hay app de reseñas** — las reseñas están hardcodeadas en la sección `varenal-reviews.liquid`. No se recolectan de clientes reales.
- **No hay blog creado** — la sección existe pero no hay contenido
- **No hay páginas estáticas** — no hay páginas de "Sobre nosotros", "Política de envío", etc.
- **No hay tracking de conversión** — no hay Google Analytics, Meta Pixel, ni TikTok Pixel configurados
- **No hay email marketing** — el formulario de newsletter del footer no está conectado a ningún servicio (Klaviyo, Mailchimp, etc.)
- **No hay chat en vivo** — no hay widget de soporte
- **No hay multi-idioma** — solo español. No hay traducción al inglés u otros idiomas
- **No hay descuentos automáticos** — no hay lógica de códigos de cupón o descuentos por volumen
- **Checkout en inglés** — se controla desde Shopify Admin → Languages, no desde el tema

---

## 12. Flujo de Trabajo

### Hacer cambios y subir

```powershell
# 1. Ir al directorio del tema
cd "C:\Users\yeval\OneDrive\Escritorio\Escritorio\My\DROPSHIPPING\2026\pagina\varenal-theme"

# 2. Editar archivos

# 3. Commit y push a GitHub (Shopify sincroniza automáticamente)
git add -A
git commit -m "descripción del cambio"
git push
```

### Subir directamente a Shopify (sin GitHub)

```powershell
shopify theme push --store ic11en-e6.myshopify.com --theme <THEME_ID> --nodelete
```

### Reconectar desde GitHub (si se pierde la conexión)

Shopify Admin → Tienda Online → Temas → Agregar tema → Conectar desde GitHub → `Ppkeash/Varenalwebs` → rama `main`

---

## 13. Historial de Commits

```
7084f3d fix: rename locale files en.default → es.default
4f84607 fix: remove invalid JSON comments from 15 files
a86ee00 fix: traducción completa al español, ajuste de envío y reseñas humanizadas
234ed38 feat: restore variant image switching + thumbnails
9863be4 revert: remove variant image switching
5c53b07 feat: variant image switching + thumbnails + price update
8f409bb Phase 7: Creative animation overhaul v3
514323d fix: comprehensive mobile responsiveness overhaul
5c15359 feat: redesign all template sections for VARENAL design consistency
6558e02 fix: auto-detect product for CTA buttons
df4f4c0 feat: connect homepage sections to Shopify product
8dbb5ba cleanup: remove 10 unused sections
ae9fc29 feat: rediseño completo VARENAL + traducción al español
c4f9d9d docs: agregar varenalreadme
b72d84f VARENAL theme - initial commit
```

---

## 14. Pendientes

- [ ] Configurar idioma español en Shopify Admin → Settings → Languages (para checkout y emails)
- [ ] Crear páginas legales: Política de envío, Política de devoluciones, Términos y condiciones, Política de privacidad
- [ ] Crear página "Sobre nosotros"
- [ ] Conectar newsletter a servicio de email (Klaviyo / Mailchimp)
- [ ] Instalar píxeles de tracking (Google Analytics, Meta Pixel)
- [ ] Crear contenido de blog para SEO
- [ ] Configurar dominio personalizado
- [ ] Considerar app de reseñas reales (Judge.me, Loox) a futuro
- [ ] **Configurar métodos de pago** y opciones de envío
- [ ] **Optimizar SEO**: meta title y description para el homepage y producto

---

## 9. Comandos de Referencia Rápida

```powershell
# Ver estado del tema en Shopify
shopify theme list --store ic11en-e6.myshopify.com

# Push completo al tema de desarrollo
shopify theme push --store ic11en-e6.myshopify.com --theme 157417144569 --nodelete

# Verificar errores Liquid
shopify theme check

# Ver estado de git
git status
git log --oneline

# Push a GitHub
git add -A && git commit -m "mensaje" && git push
```

---

## 10. URLs de Referencia

| Recurso                         | URL                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------|
| Shopify Admin                   | https://admin.shopify.com/store/ic11en-e6                                             |
| Preview del tema de desarrollo  | https://ic11en-e6.myshopify.com/?preview_theme_id=157417144569                       |
| Editor del tema                 | https://ic11en-e6.myshopify.com/admin/themes/157417144569/editor                     |
| Repositorio GitHub              | https://github.com/Ppkeash/Varenalwebs                                                |

---

*Última actualización: 22 de febrero de 2026*
