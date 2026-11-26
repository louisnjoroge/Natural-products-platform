# Product Brief — Natural Products Marketplace (working name "Asili")

_Last updated: 26 Nov 2026_

## Vision
A marketplace for Kenyan natural-product makers (soaps, shampoos, creams, gels, teas, snacks). Buyers search for a product and find the nearest makers who have it. Each maker has their own page with priced products and links to WhatsApp, Instagram and Facebook. Start in Nairobi. The same software could later serve local makers in UK/EU/US cities (local marketplaces there, **not** cross-border export).

## Core features
1. **Product-first search, near me.** Search "goat milk soap" → results sorted nearest first.
2. **Delivery: deferred.** V1 = WhatsApp / buyer and seller arrange it; maker sets the delivery fee. Later: distance-based fee estimates, courier APIs.
3. **Maker profiles.** Makers claim and verify their page. Unverified listings show "Not yet verified" and no stars until real reviews exist.
4. **Circles (co-op cover).** Makers who know each other opt in to cover each other's sold-out items: "Vera is out today; her partner Wendy has it 2 km away." The fulfilling maker packs and delivers herself.
5. **Monetisation: flat subscription, no commission.** Starter (free/low) · Pro (~KES 1,500/mo, to be validated) · Collective/Hub.
6. **Micro-ERP on paid tiers.** eTIMS-compliant invoices, stock tracking, low-stock alerts, sales summary.

## Decisions log
| Date | Decision | Why |
|---|---|---|
| 24 Nov 2026 | Availability shown as **Available / Low stock / Ask maker**, not exact counts | Makers sell on WhatsApp and at markets too, so exact counts will be stale; wrong "in stock" breaks trust |
| 24 Nov 2026 | No made-up ratings on auto-listed makers | Follower counts are not reviews; showing them as stars misleads buyers |
| 24 Nov 2026 | Show neighbourhood, not exact maker location | Many makers work from home |
| 24 Nov 2026 | Pro tier built around **KRA eTIMS invoicing** | From the 2026 year of income, all income and expenses need valid eTIMS invoices — a concrete reason to pay |
| 25 Nov 2026 | **List-first results** (2B) are the default; map is behind a List \| Map toggle | Buyers decide on product, photo and price; lists load fast on low-end phones; a sparse map looks empty early on |
| 25 Nov 2026 | Focus on Nairobi density before any other city | Marketplaces live or die on local density |

## Open questions
- Will makers pay ~KES 1,500/month? Validate with 10–20 makers using the prototype.
- How are maker profiles sourced at launch? (Recommended: manual onboarding + licensed sources like Google Places; avoid scraping Instagram/Facebook — Meta terms and Kenya Data Protection Act.)
- How does Vera benefit when Wendy fills her order, given there's no commission?
- Which licences/certifications (e.g. KEBS) to display, and what the platform requires before listing.

## Known issues in the earlier (Gemini) technical draft
To fix when the real schema is written:
- Search ranking: Pro-tier priority never applies (sort is by exact distance first).
- Search isn't fuzzy: needs `pg_trgm` + synonyms, including Swahili terms.
- Overselling: no stock reservation at checkout; stock deducted only on payment.
- Vendors matched on name-based slug — two makers with the same name merge.
- Missing tables: customers, orders, reviews, subscriptions, opt-outs.
- Circles stored as pairs, with no two-sided approval flow.
