# Product Brief — Natural Products Marketplace (working name "Asili")

_Last updated: 26 Nov 2026 (evening)_

## Guiding principle
**Asili is an aggregator.** It helps buyers find artisans and their products. It never holds stock, never takes goods on consignment, never runs premises, and never holds money for maker sales. Every feature is checked against this.

## Vision
A marketplace for Kenyan natural-product makers (soaps, shampoos, creams, gels, teas, snacks). Buyers search for a product and find the nearest makers who have it. Each maker has their own page with priced products and links to WhatsApp, Instagram and Facebook. Start in Nairobi. The same software could later serve local makers in UK/EU/US cities (local marketplaces there, **not** cross-border export).

## Core features
1. **Product-first search, near me.** Search "goat milk soap" → results sorted nearest first.
2. **Delivery: deferred.** V1 = WhatsApp / buyer and seller arrange it; maker sets the delivery fee. Later: distance-based fee estimates, courier APIs.
3. **Maker profiles.** Makers claim and verify their page. Unverified listings show "Not yet verified" and no stars until real reviews exist.
4. **Circles (co-op cover).** Makers who know each other opt in to cover each other's sold-out items: "Vera is out today; her partner Wendy has it 2 km away." The fulfilling maker packs and delivers herself.
5. **Payments go straight to makers.** Buyers pay the maker's M-Pesa Till or number. The buyer pastes the M-Pesa code; the maker taps "Received" after checking their own M-Pesa. The maker's confirmation is what counts (fake SMS screenshots are common). Later, makers with a Buy Goods Till can connect it for automatic confirmation — money still goes direct to them.
6. **"Get it for me" (premium buyer service).** Buyer builds one basket from several makers. Each maker confirms stock; the buyer pays each maker directly (code match as above); a courier partner collects and delivers one package. The buyer pays Asili one premium fee that covers coordination and the courier. Asili never handles the goods or the makers' money.

## Business model
- **Makers:** flat subscription to list products. Paid extra tier adds the micro-ERP: KRA eTIMS invoices, stock tracking, low-stock alerts, sales summary.
- **Buyers:** free to browse and buy direct. Pay a premium fee for "Get it for me".
- Asili's only income: maker subscriptions, the ERP tier, and the "Get it for me" fee (from which it pays the courier partner). No stock, no consignment, no warehouse.

## Decisions log
| Date | Decision | Why |
|---|---|---|
| 24 Nov 2026 | Availability shown as **Available / Low stock / Ask maker**, not exact counts | Makers sell on WhatsApp and at markets too, so exact counts will be stale; wrong "in stock" breaks trust |
| 24 Nov 2026 | No made-up ratings on auto-listed makers | Follower counts are not reviews; showing them as stars misleads buyers |
| 24 Nov 2026 | Show neighbourhood, not exact maker location | Many makers work from home |
| 24 Nov 2026 | Pro tier built around **KRA eTIMS invoicing** | From the 2026 year of income, all income and expenses need valid eTIMS invoices — a concrete reason to pay |
| 25 Nov 2026 | **List-first results** (2B) are the default; map is behind a List \| Map toggle | Buyers decide on product, photo and price; lists load fast on low-end phones; a sparse map looks empty early on |
| 25 Nov 2026 | Focus on Nairobi density before any other city | Marketplaces live or die on local density |
| 26 Nov 2026 | Makers receive payments directly; orders confirmed by M-Pesa code match, maker's confirmation decides | Holding buyers' money would bring payment-provider regulation and disputes; fake M-Pesa SMS are common |
| 26 Nov 2026 | Pricing: flat listing fee + paid micro-ERP (eTIMS) tier | Simple to explain; eTIMS is a legal need |
| 26 Nov 2026 | Add "Get it for me" multi-maker service at a premium | Convenience sells even when buyers could go direct (KFC on Glovo); second revenue stream |
| 26 Nov 2026 | **Aggregator only:** no hub, no consignment, no stock. "Get it for me" is partner-run: buyers pay makers directly, a courier partner delivers | Avoid overheads and stock risk; keep the business asset-light |

## Open questions
- Will makers pay ~KES 1,500/month? Validate with 10–20 makers using the prototype.
- How are maker profiles sourced at launch? (Recommended: manual onboarding + licensed sources like Google Places; avoid scraping Instagram/Facebook — Meta terms and Kenya Data Protection Act.)
- How does Vera benefit when Wendy fills her order? Options: free subscription days per covered order, or no reward (Circle activity as a trust signal).
- "Get it for me" fee: base fee, per-extra-maker fee, delivery by zone, minimum order.
- Which courier partner(s) for "Get it for me", and how pickups are booked.
- Which licences/certifications (e.g. KEBS) to display, and what the platform requires before listing.

## Known issues in the earlier (Gemini) technical draft
To fix when the real schema is written:
- Search ranking: Pro-tier priority never applies (sort is by exact distance first).
- Search isn't fuzzy: needs `pg_trgm` + synonyms, including Swahili terms.
- Overselling: no stock reservation at checkout; stock deducted only on payment.
- Vendors matched on name-based slug — two makers with the same name merge.
- Missing tables: customers, orders, reviews, subscriptions, opt-outs.
- Circles stored as pairs, with no two-sided approval flow.
