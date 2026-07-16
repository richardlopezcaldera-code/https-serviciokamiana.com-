# Revisión del sitio — MobiliarioTech (mobiliariostechchile.cl)

**Fecha:** 16 de julio de 2026
**Plataforma:** Jumpseller (plan Advanced) · Checkout v2
**Alcance:** revisión de catálogo, categorías, páginas, ventas y configuración de tienda.

> El sitio bloquea el acceso directo de bots (respuesta 403 al rastreo externo), por lo que la revisión se hizo con los datos reales de la tienda vía la integración de Jumpseller, no rascando el HTML público.

---

## Resumen ejecutivo

MobiliarioTech es una tienda sólida y bien encaminada: **750 productos**, **23 categorías** con buena estructura y descripciones optimizadas para SEO, **11 artículos de blog de calidad** con enlazado interno, WhatsApp y pasarela Flow configurados, y ventas reales entrando desde Google en varias regiones de Chile.

Hay **3 problemas prioritarios** que conviene resolver pronto porque afectan conversión, confianza legal y posicionamiento:

1. **55% del catálogo sin imágenes** (411 de 750 productos).
2. **Páginas legales aún con la plantilla demo de Jumpseller** sin completar.
3. **SKU vacío en el 65% de los productos** (487 de 750).

Ninguno es grave a nivel de "la tienda no funciona" — todo es corregible y el negocio ya vende.

---

## 🔴 Prioridad alta

### 1. Productos sin imagen — 411 de 750 (55%)
- **Todos** los productos originales (93) tienen imagen. **Todos** los que faltan (411) provienen del lote importado masivamente en 2026 (IDs de la serie 36.1M); de ese lote, 246 sí quedaron con imagen y 411 no.
- Impacto: un producto sin foto convierte muchísimo menos y **no puede publicarse en Google Shopping / Merchant Center**. Ejemplos: *Mesa Ping Pong Óptima* ($216.236), *Pizarra School Pro de Pared 120x150* ($119.070), *Mesa PP Profesional con Caja* ($209.253) — productos caros sin foto.
- **Acción sugerida:** priorizar la carga de imágenes empezando por los productos de mayor precio y los de categorías con más tráfico (Sillas, Escritorios, Mesas). Si el proveedor original tiene las fotos, se puede reimportar solo el campo imagen por SKU/nombre.

### 2. Páginas legales con plantilla demo sin completar
Las 3 páginas legales siguen con el texto de ejemplo de Jumpseller:
- **Términos y Condiciones:** dice *"MobiliarioTech se encuentra en , ."* (dirección vacía), enlaza a `mobiliariotech.jumpseller.com` en vez de `mobiliariostechchile.cl`, y conserva la frase *"Esta página de Términos y Condiciones fue creada como un ejemplo por Jumpseller."*
- **Política de reembolso:** el correo de contacto es `agencia+mobiliariotech@socialite.cl` (correo de una agencia) en lugar de `contacto@mobiliariostechchile.cl`, y la dirección de devolución está vacía.
- **Política de privacidad:** habla de *"residentes europeos"* y de transferir datos *"a Canadá y Estados Unidos"*, e incluye instrucciones tipo placeholder (*"Menciona todas las demás herramientas…"*, *"Agrega información de contacto relevante"*). No está adaptada a la normativa chilena (**Ley 19.628** y la nueva **Ley 21.719** de protección de datos).
- **Acción sugerida:** reescribir las 3 páginas con los datos reales (razón social, RUT, dirección Carmen 1865 Santiago, correo `contacto@mobiliariostechchile.cl`, WhatsApp +56 9 6154 4423), reglas reales de cambios/devoluciones y una política de privacidad acorde a la ley chilena. Falta además una página de **Contacto** y una de **Despacho/Envíos** visibles.

### 3. SKU ausente en 487 de 750 productos (65%)
- Sin SKU se complica el control de inventario, las integraciones (Google Merchant, marketplaces, ERP) y el picking en despacho. Además se detectó 1 SKU duplicado (`029`) y varios genéricos (`001`).
- **Acción sugerida:** definir un esquema de SKU (p. ej. `CAT-####`) y asignarlo, priorizando los productos que se publicarán en Google Shopping.

---

## 🟡 Prioridad media

### 4. Gestión de stock: todo en "ilimitado"
- Los **749** productos disponibles tienen `stock_unlimited = true`. La tienda **nunca marcará "agotado"**, con riesgo de vender algo sin existencias y generar cancelaciones/reembolsos.
- **Acción sugerida:** al menos para los productos que sí manejas con inventario propio, activar control de stock. Para los que son bajo pedido/proveedor, dejar claro el plazo de entrega en la ficha.

### 5. Pixel de Meta (Facebook/Instagram) no configurado
- `fb_pixel_id` está vacío. Sin pixel no hay remarketing ni medición de campañas en Meta.
- **Acción sugerida:** instalar el pixel de Meta (y verificar que Google Analytics/GA4 y Google Ads estén midiendo conversiones) antes de invertir en pauta.

### 6. Contenido demo residual
- **"Reloj de demostración"** (`demo-product`): ya no está en el catálogo activo (bien), pero tuvo 2 pedidos de prueba pagados de $500 (pedidos 1001 y 1003). Solo dejar constancia; no requiere acción.
- **"Entrada del Blog"**: publicación demo de Jumpseller, actualmente oculta. Recomendado **eliminarla**.

### 7. Carritos abandonados
- 5 de 13 pedidos quedaron abandonados, aunque **2 se recuperaron** (1010←1009, 1013←1012), lo que indica que la recuperación funciona.
- **Acción sugerida:** revisar/afinar la secuencia de correos de recuperación de carrito y considerar un cupón de recuperación. El pedido abandonado más alto fue de $239.990 (Escaño de plaza, retiro en tienda).

---

## 🟢 Lo que está bien (mantener)

- **Estructura de categorías:** 23 categorías con subcategorías coherentes y descripciones optimizadas para SEO. Muy buen trabajo.
- **Metadatos de producto:** el 100% de los productos tiene `page_title`, `meta_description` y descripción. Excelente base SEO.
- **Blog:** 11 artículos reales, bien escritos, con tono cercano y **enlazado interno** hacia categorías y entre artículos. Es un activo SEO valioso.
- **Operación:** WhatsApp (+56 9 6154 4423), Flow como pasarela, y múltiples couriers (Blue Express, Starken, envío gratis en RM).
- **Ventas reales** llegando por Google desde RM, Coquimbo, Araucanía y O'Higgins: el canal orgánico ya está trayendo clientes.

---

## Datos de ventas (agregado, sin datos personales)

| Métrica | Valor |
|---|---|
| Pedidos totales | 13 |
| Pagados | 8 (6 reales + 2 de prueba de $500) |
| Abandonados | 5 |
| Ingresos pagados reales | $340.383 CLP |
| Ticket promedio real | ~$56.731 CLP |
| Producto más vendido | Silla Ergonómica de Oficina Malla Negra 808 (~7 unidades) |
| Medio de pago | Flow |

> El detalle con datos de clientes **no** se guardó en este repositorio por decisión del titular. Puede exportarse aparte desde el panel de Jumpseller cuando se necesite.

---

## Plan de acción sugerido (orden recomendado)

1. **Cargar imágenes** de los 411 productos sin foto (empezar por los de mayor precio y más tráfico).
2. **Reescribir las 3 páginas legales** + crear páginas de Contacto y Despacho.
3. **Asignar SKU** a los productos (prioridad: los que van a Google Shopping).
4. **Configurar stock real** en los productos con inventario propio.
5. **Instalar pixel de Meta** y verificar medición GA4/Google Ads.
6. **Eliminar** la entrada de blog demo y afinar recuperación de carritos.

---

*Revisión generada a partir del respaldo del 2026-07-16. Los datos de origen están en `mobiliariostechchile-backup/data/`.*
