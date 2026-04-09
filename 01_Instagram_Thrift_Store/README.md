# Instagram Thrift Store — Database Design

An ER diagram for a small Instagram-based store selling thrifted and handmade fashion items. The database supports product management, order tracking, payments, and shipping.

## Entities

| Entity | Purpose |
|---|---|
| `customers` | Stores buyer info (name, email, phone, address) |
| `orders` | Tracks each order placed by a customer |
| `order_items` | Junction table — links orders to product variants |
| `products` | Base product record (thrift or handmade) |
| `product_variants` | Size and color variants per product |
| `thrift_details` | Extra details for thrift-only items (condition, brand, availability) |
| `handmade_details` | Extra details for handmade items (stock, material, batch size) |
| `payments` | Payment status and method per order |
| `shipping` | Shipping status and tracking per order |

## Key Design Decisions

- `product_type` field on `products` distinguishes thrift vs handmade items.
- `thrift_details` and `handmade_details` are optional (0..1) sub-tables — only one applies per product.
- Thrift items have an `is_available` boolean since they are unique, one-of-a-kind pieces.
- `unit_price` is stored in `order_items` (not products) to preserve historical pricing.
- `shipping` is linked to `orders`, not individual items, reflecting how this business ships.

## Relationships

- A customer can place multiple orders (1:N)
- An order can contain multiple products via `order_items` (M:N resolved)
- Each order has one payment record (1:1)
- Each order has one shipping record (1:0..1)
