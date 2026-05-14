# Kreas Shop API — Mock Product Catalog

Static JSON dataset for a Vue.js mobile-first e-commerce app.
24 products across 4 categories — no backend, no authentication required.

## Endpoint

```
GET https://raw.githubusercontent.com/Anita-Liberatore/kreas-shop-api/master/products.json
```

## Usage

```js
const res      = await fetch('https://raw.githubusercontent.com/Anita-Liberatore/kreas-shop-api/master/products.json')
const products = await res.json()
// → Array of 24 product objects
```

---

## Product schema

```json
{
  "id": 1,
  "name": "Sneakers Urban Pro",
  "category": "Footwear",
  "price": 89.99,
  "description": "Sneakers urbane leggere con suola in gomma antiscivolo...",
  "image": "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=600&q=80"
}
```

| Field | Type | Description |
|-------|------|-------------|
| `id` | number | Unique identifier |
| `name` | string | Product name |
| `category` | string | `Footwear` · `Clothing` · `Accessories` · `Electronics` |
| `price` | number | Price in EUR |
| `description` | string | Short product description |
| `image` | string | Unsplash image URL (600px wide) |

---

## Discount rule

> If the customer adds **more than 3 products** to the cart, a **10% discount** is applied to the total.

```js
const total    = cart.reduce((sum, item) => sum + item.price, 0)
const discount = cart.length > 3 ? total * 0.10 : 0
const final    = total - discount
```

In Vue 3 with computed properties:

```js
const total    = computed(() => cart.value.reduce((s, i) => s + i.price, 0))
const discount = computed(() => cart.value.length > 3 ? total.value * 0.10 : 0)
const final    = computed(() => total.value - discount.value)
```

---

## App requirements

Build a **mobile-first Vue.js app** with 3 views:

| View | Description |
|------|-------------|
| **Product list** | Grid of all products fetched from the API |
| **Product detail** | Full page for a single product with add-to-cart button |
| **Cart** | List of selected items, subtotal, discount (if applicable) and final total |

**Tips:**
- Use Chrome DevTools with a smartphone preset to develop mobile-first
- Use `bootstrap-vue-next` or plain Bootstrap 5 for layout
- Bonus: make the layout responsive and adapt it to desktop as well

---

## Products catalog

| # | Name | Category | Price |
|---|------|----------|-------|
| 1 | Sneakers Urban Pro | Footwear | €89.99 |
| 2 | Felpa Oversize Essential | Clothing | €54.99 |
| 3 | Cuffia Bluetooth Studio | Electronics | €129.00 |
| 4 | Zaino Explorer 30L | Accessories | €69.99 |
| 5 | Smartwatch Fitness X1 | Electronics | €199.00 |
| 6 | T-Shirt Essential Pack | Clothing | €34.99 |
| 7 | Occhiali da Sole Retro | Accessories | €49.99 |
| 8 | Giacca Softshell Trail | Clothing | €119.00 |
| 9 | Portafoglio Slim Leather | Accessories | €39.99 |
| 10 | Cap Logo Ricamato | Accessories | €24.99 |
| 11 | Chelsea Boots in Pelle | Footwear | €149.00 |
| 12 | Running Shoes Pace 2.0 | Footwear | €109.99 |
| 13 | Jeans Slim Tapered | Clothing | €74.99 |
| 14 | Borraccia Termica 500ml | Accessories | €29.99 |
| 15 | Stivali da Trekking Alpine | Footwear | €179.00 |
| 16 | Maglione Collo Alto | Clothing | €89.99 |
| 17 | Camicia Oxford Button-Down | Clothing | €59.99 |
| 18 | Blazer Strutturato | Clothing | €139.00 |
| 19 | Cappotto Camel Oversize | Clothing | €219.00 |
| 20 | Auricolari TWS Pro | Electronics | €89.99 |
| 21 | Sandali Comfort Plus | Footwear | €49.99 |
| 22 | Sciarpa Cashmere Blend | Accessories | €64.99 |
| 23 | Slip-On Canvas | Footwear | €39.99 |
| 24 | Speaker Portatile 360° | Electronics | €79.99 |
