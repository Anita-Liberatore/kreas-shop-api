# Kreas Shop API — Mock Food Catalog

Static JSON dataset for a Vue.js mobile-first e-commerce app focused on Italian food products.
24 products across 6 categories — no backend, no authentication required.

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
  "name": "Pomodori Cuore di Bue",
  "category": "Frutta & Verdura",
  "price": 3.50,
  "description": "Pomodori cuore di bue coltivati in pieno campo...",
  "image": "https://images.unsplash.com/photo-1592924357228-91a4daadcfea?w=600&q=80"
}
```

| Field | Type | Description |
|-------|------|-------------|
| `id` | number | Unique identifier |
| `name` | string | Product name |
| `category` | string | `Frutta & Verdura` · `Pane & Dolci` · `Latticini` · `Carne & Pesce` · `Bevande` · `Dispensa` |
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
| 1 | Pomodori Cuore di Bue | Frutta & Verdura | €3.50 |
| 2 | Fragole Bio Campane | Frutta & Verdura | €4.99 |
| 3 | Arance Tarocco Siciliane | Frutta & Verdura | €3.20 |
| 4 | Insalata Mista Bio | Frutta & Verdura | €2.50 |
| 5 | Pane di Altamura DOP | Pane & Dolci | €4.50 |
| 6 | Croissant al Burro | Pane & Dolci | €1.80 |
| 7 | Torta al Cioccolato Fondente | Pane & Dolci | €14.90 |
| 8 | Biscotti di Prato | Pane & Dolci | €5.50 |
| 9 | Mozzarella di Bufala DOP | Latticini | €4.20 |
| 10 | Parmigiano Reggiano 24 mesi | Latticini | €9.90 |
| 11 | Yogurt Greco Bio | Latticini | €2.80 |
| 12 | Burro di Montagna | Latticini | €3.50 |
| 13 | Bistecca di Fassona Piemontese | Carne & Pesce | €18.90 |
| 14 | Salmone Norvegese Affumicato | Carne & Pesce | €12.50 |
| 15 | Prosciutto di Parma DOP | Carne & Pesce | €13.90 |
| 16 | Pollo Ruspante Allevato a Terra | Carne & Pesce | €9.90 |
| 17 | Caffè Specialty Etiopia | Bevande | €12.90 |
| 18 | Succo di Melagrana Biologico | Bevande | €5.50 |
| 19 | Chianti Classico DOCG | Bevande | €16.90 |
| 20 | Acqua Minerale Effervescente 6×1.5L | Bevande | €3.80 |
| 21 | Pasta di Gragnano IGP | Dispensa | €3.20 |
| 22 | Olio Extra Vergine di Oliva DOP | Dispensa | €13.90 |
| 23 | Salsa di Pomodoro Artigianale | Dispensa | €3.50 |
| 24 | Miele Millefiori di Acacia | Dispensa | €8.90 |
