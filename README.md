# 🛍️ MyZone — Tech E-Commerce Store

A modern, responsive e-commerce web app built with **React** for browsing and purchasing tech products. Features real-time filtering, a cart sidebar, wishlist, and a dark/light theme toggle.

---

## 🚀 Tech Stack

- **React** (Functional Components + Hooks)
- **Vite** (recommended dev server)
- **CSS** (custom properties for theming)
- **LocalStorage** (theme persistence)

---

## ✨ Features

- 🔍 **Live Search** — Filter products by name in real time
- 🏷️ **Brand Filter** — Browse by specific brands (Apple, Dell, HP, etc.)
- 📊 **Sort Options** — Sort by price (low→high, high→low) or rating
- 🛒 **Cart Sidebar** — Add/remove items, adjust quantities, view subtotal
- ❤️ **Wishlist** — Save favourite products with a single click
- 🌙 **Theme Toggle** — Switch between dark and light mode (persisted via localStorage)
- 📱 **Responsive Design** — Works across desktop and mobile

---

## 📁 Project Structure

```
src/
├── App.jsx                        # Root component — all state lives here
├── App.css
├── components/
│   ├── NavBar/
│   │   ├── NavLogo.jsx            # Brand logo + home link
│   │   ├── NavLinks.jsx           # Products / Support / About links
│   │   ├── Toggle.jsx             # Dark/light theme switcher
│   │   ├── Wishlist.jsx           # Wishlist icon with badge
│   │   ├── Cart.jsx               # Cart icon with badge
│   │   └── SignButtons.jsx        # "Shop Now" CTA button
│   ├── HeroSection/
│   │   └── Hero.jsx               # Hero banner with stats
│   ├── Sections/
│   │   ├── BestSeller.jsx         # Products grid + filters bar
│   │   ├── ProductCard.jsx        # Individual product card
│   │   ├── UserControlls.jsx      # Cart sidebar overlay
│   │   └── Footer.jsx             # Footer
│   └── demo.js                    # Mock product data (30+ products)
```

---

## 🧠 How It Works

### State Management
All state is managed in `App.jsx` and passed down as props:

| State | Type | Purpose |
|---|---|---|
| `cartItems` | Array | Products in cart with quantities |
| `wishlist` | Array | Product IDs that are wishlisted |
| `searchTerm` | String | Current search query |
| `selectedBrand` | String | Active brand filter |
| `sortBy` | String | Active sort option |
| `isCartOpen` | Boolean | Cart sidebar visibility |
| `theme` | String | `"dark"` or `"light"` |

### Filtering & Sorting Pipeline
```
products (demo.js)
  → filter by searchTerm
  → filter by selectedBrand
  → sort by sortBy
  → pass as filteredProducts to <BestSeller />
```

### Cart Logic
- **Add:** If item exists, increment quantity; otherwise push `{...product, quantity: 1}`
- **Update:** Adjust quantity; if `<= 0`, remove item
- **Totals:** `cartCount` sums all quantities; `cartTotal` sums `price × quantity`

### Theme System
```js
// Initialized from localStorage, falls back to "dark"
const [theme, setTheme] = useState(() =>
  localStorage.getItem("myzone-theme") || "dark"
);

// Applied via data attribute on <html>
document.documentElement.setAttribute("data-theme", theme);
```

---

## 🛠️ Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/your-username/myzone.git
cd myzone

# 2. Install dependencies
npm install

# 3. Start the dev server
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

---

## 📦 Product Data Format (`demo.js`)

```js
{
  id: 1,
  name: "MacBook Pro 14",
  brand: "Apple",
  price: 189999,
  originalPrice: 209999,
  discount: "10% OFF",
  rating: 4.8,
  image: "url-to-image",
  isBestSeller: true
}
```

---

## 🔮 Future Improvements

- [ ] User authentication (login / signup)
- [ ] Backend API integration
- [ ] Checkout & payment flow
- [ ] Product detail pages
- [ ] Persistent cart via localStorage
- [ ] Ratings & reviews

---

## 📄 License

MIT © 2026 MyZone
