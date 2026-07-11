# Inspección de la respuesta cruda del feed — MobiliarioTech

**Fecha de inspección:** 2026-07-11
**Tienda:** MobiliarioTech (plataforma Jumpseller, plan Pro)
**URL real:** `https://mobiliariostechchile.cl`

> ⚠️ **Hallazgo importante:** el CRM (`kamiana-crm-pro (1).html`) tenía configurado
> `www.mobiliariostecchile.cl` (sin la "h" de "tech"). El dominio correcto es
> `mobiliariostechchile.cl`. Ya fue corregido en `EMP.web`.

## Datos de la tienda (respuesta cruda de `get_store_info`)

```json
{
  "store": {
    "name": "MobiliarioTech",
    "code": "mobiliariotech",
    "currency": "CLP",
    "country": "CL",
    "timezone": "America/Santiago",
    "email": "Kamianaspa2023@gmail.com",
    "url": "https://mobiliariostechchile.cl",
    "address": { "address": "Carmen 1865", "city": "Santiago", "region": "Región Metropolitana" },
    "subscription_plan": "pro",
    "whatsapp_phone": "56961544423",
    "checkout_version": "v2"
  }
}
```

## Estructura cruda de un producto del feed (API Jumpseller)

Cada elemento del feed viene envuelto en una clave `product`:

```json
{
  "product": {
    "id": 34790052,
    "name": "Sillon de oficina KM 5050",
    "page_title": "Sillon de oficina KM 5050",
    "description": "Esta silla incorpora... <br>\n-Armazón de nylon... (HTML embebido)",
    "meta_description": "…",
    "price": 56990.0,
    "cost_per_item": null,
    "compare_at_price": null,
    "weight": 12.0,
    "stock": 0,
    "stock_unlimited": true,
    "sku": "001",
    "brand": "Mobitech",
    "barcode": null,
    "featured": true,
    "status": "available",
    "type": "physical",
    "created_at": "2026-03-30 20:23:16 UTC",
    "updated_at": "2026-04-07 23:35:48 UTC",
    "length": 51.0, "width": 60.0, "height": 82.0,
    "quotable": true,
    "categories": [ { "id": 2593906, "name": "Sillas", "parent_id": null } ],
    "images": [ { "id": 75356225, "url": "https://images.jumpseller.com/store/mobiliariotech/...jpg", "position": 1 } ],
    "variants": [],
    "fields": [],
    "permalink": "sillon-de-oficina-km-5050",
    "discount": "0.0",
    "currency": "CLP"
  }
}
```

### Puntos clave detectados en la respuesta cruda

| Detalle | Implicación para el script |
|---|---|
| Envoltura `{ "product": { … } }` por elemento | El script debe desempaquetar `x.product` antes de mapear |
| `description` contiene HTML (`<br>`, `<p>`) | Hay que limpiar etiquetas antes de mostrarla en el CRM |
| `price` es número decimal en CLP | Redondear a entero para el CRM (`Math.round`) |
| `stock: 0` pero `stock_unlimited: true` | El stock real no está gestionado; no tratar 0 como "sin stock" |
| `cost_per_item: null` | El costo no está cargado en la tienda; queda en 0 en el CRM |
| `status` puede ser `available` o `not-available` | Filtrar según lo que se quiera importar |
| `categories` es un array (puede venir vacío) | Usar `categories[0].name` con valor por defecto |
| `brand` puede ser `null` | Valor por defecto vacío |

## Mapeo Jumpseller → `DB.productos` del CRM

| Campo CRM | Campo del feed | Transformación |
|---|---|---|
| `id` | `product.id` | `"P" + últimos 5 dígitos` |
| `nombre` | `product.name` | directo |
| `sku` | `product.sku` | directo |
| `cat` | `product.categories[0].name` | por defecto `"Muebles"` |
| `marca` | `product.brand` | por defecto `""` |
| `precio` | `product.price` | `Math.round` |
| `costo` | `product.cost_per_item` | `null` → `0` |
| `stock` | `product.stock` | directo (ver nota de `stock_unlimited`) |
| `desc` | `product.description` | quitar HTML, truncar a 300 chars |
| `specs` | `weight/length/width/height` | formatear con unidades (`kg`, `cm`) |

## Cómo usar el inspector

1. Abrir `feed-inspector.html` en el navegador.
2. Elegir una URL de feed (viene precargada la del feed Google Shopping: `https://mobiliariostechchile.cl/products/feed`).
3. Revisar: estado HTTP, cabeceras, cuerpo crudo, estructura detectada (JSON o XML) y campos disponibles.
4. Si la estructura es reconocida, la sección 5 genera el snippet listo para pegar en `DB.productos` del CRM.

**Nota CORS:** si el navegador bloquea la lectura (error de red), el feed probablemente existe igual —
verificar en DevTools → Network o con `curl -i <url>`. En ese caso el script del CRM necesitará
consumir el feed desde un backend o proxy propio, no directamente desde el navegador.
