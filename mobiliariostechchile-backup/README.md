# Respaldo y revisión — MobiliarioTech (mobiliariostechchile.cl)

Respaldo del contenido de la tienda **MobiliarioTech** (Jumpseller) y su revisión.

- **Fecha del respaldo:** 2026-07-16
- **Tienda:** MobiliarioTech · https://mobiliariostechchile.cl
- **Plataforma:** Jumpseller (plan Advanced)

## Contenido

| Archivo | Descripción |
|---|---|
| [`REVISION.md`](REVISION.md) | Revisión completa con hallazgos priorizados y plan de acción. |
| [`data/products.json`](data/products.json) | 750 productos con toda su ficha (precio, descripción, meta, categorías, imágenes, etc.). |
| [`data/categories.json`](data/categories.json) | 23 categorías y subcategorías con sus permalinks y descripciones SEO. |
| [`data/pages.json`](data/pages.json) | Índice de las 15 páginas (3 legales + 12 de blog). |
| [`data/store.json`](data/store.json) | Configuración de la tienda (token de webhooks redactado). |
| [`data/ventas-resumen.json`](data/ventas-resumen.json) | Resumen agregado de ventas **sin datos personales**. |

## Notas de privacidad

- **No** se incluyen datos personales de clientes (nombres, direcciones, correos, teléfonos) ni pedidos individuales, por decisión del titular. Solo hay un resumen de ventas agregado.
- El `hooks_token` de la tienda se guardó como `__REDACTADO__` porque es un secreto; el valor real está en el panel de Jumpseller.

## Cómo regenerar / actualizar el respaldo

Los datos se obtienen desde la integración de Jumpseller (productos, categorías, páginas, configuración). Para un respaldo nativo completo (incluyendo temas/plantillas), usar también **Exportar** desde el panel de Jumpseller.

## Hallazgos principales (resumen)

1. 🔴 411 de 750 productos (55%) **sin imagen** — todos del lote importado en 2026.
2. 🔴 Las 3 **páginas legales** siguen con la plantilla demo de Jumpseller sin completar.
3. 🔴 **SKU vacío** en 487 de 750 productos (65%).
4. 🟡 Todo el stock está en "ilimitado"; sin pixel de Meta; carritos abandonados.
5. 🟢 Muy buena estructura de categorías, metadatos completos y blog de calidad.

Ver el detalle en [`REVISION.md`](REVISION.md).
