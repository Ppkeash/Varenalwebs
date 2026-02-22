# varenalreadme

Documentación completa del proyecto VARENAL — tema Shopify personalizado para el masajeador de tobillo con calor inalámbrico.

---

## 1. Visión General del Proyecto

**Marca:** VARENAL  
**Producto:** Masajeador de tobillo con calor inalámbrico (Electric Ankle Heating Massage Pad)  
**Objetivo:** Construir una tienda de dropshipping global de bienestar, comenzando con este producto.  
**Idioma del tema:** Español  
**Estado actual:** Tema completo subido a GitHub y empujado a Shopify como tema de desarrollo.

---

## 2. Identidad de Marca

| Elemento       | Valor                          |
|----------------|-------------------------------|
| Color primario | `#2db5a3` (verde azulado)     |
| Color secundario | `#5bc87a` (verde)           |
| Color acento   | `#16a085` (verde oscuro)      |
| Color de texto | `#1a1a2e` (casi negro)        |
| Fuente títulos | Poppins (peso 600)            |
| Fuente cuerpo  | Work Sans (peso 400)          |

### Especificaciones del Producto
- 3 niveles de calor: 48°C / 53°C / 58°C
- Vibración terapéutica
- Pantalla LED táctil
- Batería 2000mAh (inalámbrico)
- Apagado automático a los 15 minutos
- Forro de felpa suave
- Diseño universal (ambos tobillos)

---

## 3. Infraestructura Técnica

### Herramientas Instaladas
| Herramienta      | Versión     |
|------------------|-------------|
| Node.js          | v22.15.0    |
| npm              | 10.9.0      |
| Git              | 2.49.0      |
| Shopify CLI      | v3.91.0     |

### Shopify
- **Tienda:** `ic11en-e6.myshopify.com`
- **Cuenta:** `valbuenaesteban19@gmail.com`
- **ID del tema de desarrollo:** `157417144569`
- **Nombre del tema:** `Development (648e0b-Ppkeash)`
- **Tema activo publicado (preinstalado):** Dwell (`ID: 157405217017`) — aún en vivo al momento del último push

> **Nota:** Existe un tercer tema roto llamado "VARENAL" (creado por un push fallido con `--unpublished`). Muestra una página 404 y debe ser eliminado desde el Admin de Shopify → Temas.

### GitHub
- **Repositorio:** `https://github.com/Ppkeash/Varenalwebs`
- **Cuenta GitHub:** `Ppkeash`
- **Rama principal:** `main`
- **Último commit:** `b72d84f` — "VARENAL theme - Masajeador de tobillo con calor inalámbrico (tema completo en español)"

### Directorio Local
```
C:\Users\yeval\OneDrive\Escritorio\Escritorio\My\DROPSHIPPING\2026\pagina\varenal-theme\
```

---

## 4. Estructura del Tema

El tema está basado en el skeleton de **Dawn** (Shopify CLI v3), con todas las secciones personalizadas para VARENAL.

```
varenal-theme/
├── assets/
│   └── critical.css              # CSS de marca VARENAL (colores, botones, animaciones)
├── blocks/
│   ├── group.liquid
│   └── text.liquid
├── config/
│   ├── settings_data.json        # Datos de configuración activos (colores, fuentes)
│   └── settings_schema.json      # Esquema de personalización del tema
├── layout/
│   ├── theme.liquid              # Layout principal (meta tags, fuentes, favicon)
│   └── password.liquid
├── locales/
│   ├── en.default.json
│   └── en.default.schema.json
├── sections/
│   ├── hero-banner.liquid        # Hero con CTA principal
│   ├── trust-bar.liquid          # Barra de estadísticas de confianza
│   ├── features-grid.liquid      # 6 tarjetas de características del producto
│   ├── product-showcase.liquid   # 3 bloques alternados con imagen y texto
│   ├── how-it-works.liquid       # 3 pasos de uso
│   ├── testimonials.liquid       # 3 reseñas de clientes
│   ├── faq-accordion.liquid      # 6 preguntas frecuentes
│   ├── cta-banner.liquid         # Banner de llamada a la acción con gradiente
│   ├── announcement-bar.liquid   # Barra superior de anuncio
│   ├── product.liquid            # Página de producto personalizada
│   ├── header.liquid             # Cabecera sticky con logo, hamburguesa, carrito
│   ├── footer.liquid             # Pie de página 4 columnas + newsletter
│   ├── header-group.json         # Configuración del grupo de cabecera
│   ├── footer-group.json         # Configuración del grupo de pie
│   └── [otras secciones base]    # 404, article, blog, cart, collection, etc.
├── snippets/
│   ├── css-variables.liquid      # Variables CSS con colores y fuentes de marca
│   ├── image.liquid
│   └── meta-tags.liquid
├── templates/
│   ├── index.json                # Homepage con 8 secciones en español
│   ├── product.json
│   └── [otras templates]
├── .gitignore
├── .gitattributes
├── .shopifyignore
├── .theme-check.yml
└── varenalreadme.md              # Este archivo
```

---

## 5. Secciones del Homepage (index.json)

El homepage está compuesto por las siguientes secciones en orden:

1. **hero** (`hero-banner`) — "Alivia el Dolor de Tobillo con Calor Terapéutico y Vibración"
2. **trust_bar** (`trust-bar`) — Clientes Felices / Valoración 4.8★ / Garantía 30 días / Envío Mundial
3. **features** (`features-grid`) — 6 características: Calor, Apagado Auto, Inalámbrico, LED Táctil, Ajuste Universal, Larga Batería
4. **showcase** (`product-showcase`) — Alivio Localizado / Diseño Inteligente / Confort Premium
5. **how_it_works** (`how-it-works`) — Envuelve / Elige / Relájate (3 pasos)
6. **testimonials** (`testimonials`) — Sara M. / Jaime R. / María L.
7. **faq** (`faq-accordion`) — 6 preguntas frecuentes sobre el producto
8. **cta** (`cta-banner`) — "¿Listo Para Sentir la Diferencia? — Pedir Ahora, Envío Gratis"

---

## 6. Bugs Resueltos

### Bug 1: Error de sintaxis Liquid en product-showcase.liquid
**Problema:** `{% if forloop.index0 | modulo: 2 == 1 %}` — Liquid no soporta filtros con operadores de comparación en la misma expresión.  
**Solución:**
```liquid
{% assign row_mod = forloop.index0 | modulo: 2 %}
{% if row_mod == 1 %}
```

### Bug 2: Servidor de desarrollo (`shopify theme dev`) con ERR_CONNECTION_REFUSED
**Problema:** El servidor local nunca fue accesible en ningún puerto (3000, 9292, 4000). Probablemente relacionado con OneDrive, firewall, o el path con espacios.  
**Solución adoptada:** Usar `shopify theme push` directamente en lugar del servidor de desarrollo. Funciona sin problemas.

### Bug 3: Tema roto "VARENAL" con página 404
**Problema:** Un push con `--unpublished` creó un tema vacío que muestra 404.  
**Solución pendiente:** Eliminar manualmente desde Shopify Admin → Temas.

### Bug 4: Codificación en PowerShell
**Problema:** `Set-Content` puede corromper emojis (✨ → `?`, ★ → `?`) si no se especifica `-Encoding UTF8`.  
**Estado:** Los archivos finales están correctos (verificado con grep). No hubo corrupción real.

---

## 7. Flujo de Trabajo para Futuras Actualizaciones

### Editar el tema localmente y subir a Shopify:
```powershell
# 1. Ir al directorio del tema
cd "C:\Users\yeval\OneDrive\Escritorio\Escritorio\My\DROPSHIPPING\2026\pagina\varenal-theme"

# 2. Hacer cambios en los archivos

# 3. Verificar que no hay errores Liquid
shopify theme check

# 4. Subir a Shopify (sin sobreescribir archivos del editor)
shopify theme push --store ic11en-e6.myshopify.com --theme 157417144569 --nodelete

# 5. Guardar cambios en GitHub
git add -A
git commit -m "descripción del cambio"
git push
```

### Para publicar el tema como activo (hacer que los visitantes lo vean):
Shopify Admin → Tienda Online → Temas → Tema `Development (648e0b-Ppkeash)` → **Publicar**

### Importar desde GitHub a Shopify (si se reinicia el entorno):
Shopify Admin → Tienda Online → Temas → Agregar tema → **Conectar desde GitHub** → Seleccionar repo `Ppkeash/Varenalwebs` → Rama `main`

---

## 8. Pendientes

- [ ] **Publicar el tema** como activo (reemplazar el tema Dwell)
- [ ] **Eliminar el tema "VARENAL" roto** (el que muestra 404) desde Shopify Admin
- [ ] **Subir logo de VARENAL** en el personalizador del tema (formato SVG o PNG transparente recomendado)
- [ ] **Subir imágenes del producto** al tema (hero banner image, imágenes del product-showcase)
- [ ] **Crear el producto** en Shopify Admin → Productos → Agregar producto (con variantes de talla/color)
- [ ] **Cambiar nombre de la tienda** de "Mi tienda" a "VARENAL" en Configuración → General
- [ ] **Configurar dominio** personalizado si aplica
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
