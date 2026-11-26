# Natural Products Platform (working name "Asili")

A marketplace that helps buyers in Nairobi find natural products (soaps, body care, teas, snacks) from the nearest local makers, and gives makers simple tools to sell, invoice and track stock.

## What's here

| Folder | What it is |
|---|---|
| [`docs/`](docs/product-brief.md) | Product brief, decisions log and open questions |
| [`prototype/`](prototype/index.html) | Clickable mobile prototype of the buyer app (static HTML, sample data) |

## Prototype screens

Brand & first impression: `index.html` (welcome: shopping or making), `for-buyers.html`, `for-makers.html`, `logo.html`.

1. `app.html` — Home: search first, categories, makers near you
2. `results.html` — Results list, nearest first (default), with List | Map toggle
3. `map.html` — Map view of the same results
4. `maker.html` — Maker page with WhatsApp / Instagram / Facebook and Circle partners
5. `product.html` — Sold out → a Circle partner covers the order
6. `checkout.html` — Delivery choice; buyer pays the maker directly and confirms with the M-Pesa code
6b. `basket.html` — "Get it for me" (premium): multi-maker basket; buyer pays makers directly, a courier partner delivers

Maker app (Pro tier):

7. `maker-home.html` — Today: open/closed, new orders, alerts, weekly summary
8. `maker-stock.html` — Quick stock update (Available / Low / Out)
9. `maker-invoice.html` — KRA eTIMS invoice with M-Pesa request
10. `maker-circle.html` — Circle partners, invites and cover settings

`screens.html` lists every screen in one place.

All makers, prices and ratings in the prototype are **sample data**.

## Viewing the prototype

- **Locally:** open `prototype/index.html` (welcome) or `prototype/screens.html` (all screens) in a browser (best at phone width).
- **Online:** published with GitHub Pages via `.github/workflows/pages.yml` once Pages is enabled (Settings → Pages → Source: GitHub Actions).

## Planned stack (not built yet)

- Database, auth, storage: Supabase (PostgreSQL + PostGIS)
- Web app: deployed from this repo to Vercel or Netlify
- Payments: buyers pay makers directly; orders confirmed by M-Pesa code match (maker confirms). Optional later: makers connect their own Till via Daraja for automatic confirmation. Asili never holds stock or makers' money; it only charges its own "Get it for me" fee.
- Tax invoices: KRA eTIMS
