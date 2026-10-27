# Data / Datos

The source files are **not included** in this repository. The notebook expects five JSON-lines files in this folder with the schemas below.
*ES: los archivos fuente **no se incluyen** en este repositorio. El notebook espera cinco archivos JSON (un objeto por línea) en esta carpeta con los siguientes schemas.*

| File | Fields | Notes |
|---|---|---|
| `customers.json` | `customer_id` (long), `customer_code`, `name`, `age`, `country`, `segment`, `signup_date` (string `yyyy-MM-dd`), `active` (boolean) | Customer master |
| `products.json` | `product_id` (long), `sku`, `product_name`, `brand`, `category`, `list_price` (double) | Product catalog |
| `orders_jan_mar.json` | `order_id`, `customer_id` (long), `order_ts` (ISO string), `status`, `channel`, `payment_method`, `discount` (double), `items` (array of `{product_id, quantity, unit_price}`) | Numeric types |
| `orders_apr_jun.json` | Same fields as above | `customer_id`, `discount`, `quantity`, `unit_price` arrive as **strings** (schema drift) |
| `digital_events.json` | `event_id`, `customer_id` (string), `event_ts` (ISO string), `event_type` (`view`, `add_to_cart`, `purchase`), `device` `{type, os}`, `attributes` `{campaign, source}`, `items` (array of `{product_id, quantity}`) | Nested structs and arrays |

**Channels / Canales:** `WEB`, `APP`, `STORE`, `CALL_CENTER` · **Statuses / Estados:** `COMPLETED`, `CANCELLED`, `RETURNED`

The notebook handles duplicates, nulls, schema drift, orphan references and empty arrays — see section 2.5 of the notebook.
