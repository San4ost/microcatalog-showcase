# MicroCatalog — price comparison for electronic components

Live: https://microcatalog.san4osvsp.workers.dev/ua

A Ukrainian-language website that shows where to buy an electronic component (IC, transistor, diode, module) at the
lowest price. Ukrainian shops are compared against AliExpress by the **landed price**, i.e. the price including
delivery. The source code lives in a private repository; this page describes the project.

## What the site offers

- **Part catalog** grouped by category (power ICs, transistors, diodes, interfaces and more), UI in Ukrainian.
- **Part page**: photo, package, specifications and a list of shop offers with price, stock status and delivery time.
- **Kits and assortments** that contain the part, shown as a separate horizontally scrolling strip under the price list.
- **Search** by part number and name.
- **Fresh data**: prices and stock are delivered by a separate scraper (MegaMicroParser); the site only shows what the
  scraper has verified.

## How it is built

- The site and the scraper communicate only through a shared PostgreSQL database (Supabase). The schema evolves through
  migrations kept in the site repository.
- Only verified offers are shown. A shop listing whose match to a catalog part is uncertain stays hidden until reviewed.
- Part photos are stored in Supabase Storage (public bucket).
- Deployed on Cloudflare Workers.

## Related project

[megamicroparser-showcase](https://github.com/San4ost/megamicroparser-showcase) — the price scraper behind the data:
13 shops, product-to-catalog matching, catalog growth, photos, specifications and datasheets.
