# Natural Products Platform (working name "Asili")

A marketplace that helps buyers in Nairobi find natural products (soaps, body care, teas, snacks) from the nearest local makers, and gives makers simple tools to sell, invoice and track stock.

## What's here

| Folder | What it is |
|---|---|
| [`docs/`](docs/product-brief.md) | Product brief, decisions log and open questions |
| [`prototype/`](prototype/index.html) | Clickable mobile prototype of the buyer app (static HTML, sample data) |

## Prototype screens

1. `index.html` — Home: search first, categories, makers near you
2. `results.html` — Results list, nearest first (default), with List | Map toggle
3. `map.html` — Map view of the same results
4. `maker.html` — Maker page with WhatsApp / Instagram / Facebook and Circle partners
5. `product.html` — Sold out → a Circle partner covers the order
6. `checkout.html` — Delivery choice and M-Pesa payment

All makers, prices and ratings in the prototype are **sample data**.

## Viewing the prototype

- **Locally:** open `prototype/index.html` in a browser (best at phone width).
- **Online:** published with GitHub Pages via `.github/workflows/pages.yml` once Pages is enabled (Settings → Pages → Source: GitHub Actions).

## Planned stack (not built yet)

- Database, auth, storage: Supabase (PostgreSQL + PostGIS)
- Web app: deployed from this repo to Vercel or Netlify
- Payments: M-Pesa Daraja API · Tax invoices: KRA eTIMS
