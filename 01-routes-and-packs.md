# 01 — Routes & packs

> Status: **scaffold only.** Route list, pack size, and lead drivers
> are still to be selected. This file documents the *structure* the
> event will use; populate the route table once routes are chosen.

## Pack model

- Each route runs with a **staff lead driver** at the front.
- Cars are grouped into **packs** of N (TBD per route).
- Packs depart in sequence, gap between packs TBD.
- Same pack structure as TCSS 2026 — see
  `4-Admin/summer-stage-check-in/Master List - TCSS 2026.xlsx` for
  reference.

## Capacity (initial)

- **Route cap: 150 cars per route.** Set 2026-06-21.
- A single driver-ticket = one car entry for one route.
- The Friday long route and the two Saturday short routes each
  cap independently at 150 cars. So **total route-ticket ceiling =
  150 cars × 3 routes = 450 driver-route-tickets** (though most
  drivers will buy the multi-route bundle, so total *tickets sold*
  will be lower than 450).
- Pack size per route is still TBD and will be set by road
  conditions, sweep vehicle, and lead driver availability. Packs
  run sequentially within a route.

## Route list

**3 routes total: 1 long (Friday) + 2 short (Saturday).** This is
the minimum to support the 3-tier $75/$60/$50 pricing in
`02-pricing-tiers.md`.

| # | Day | Time (CT) | Duration | Type | Name | Length | Pack size | Lead driver | Hazards noted |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Fri Oct 2 | 10:00 AM – 4:00 PM | 6 hrs | Long | TBD | TBD | TBD | TBD | TBD |
| 2 | Sat Oct 3 | 8:00 AM – 1:00 PM | 5 hrs | Short | TBD | TBD | TBD | TBD | TBD |
| 3 | Sat Oct 3 | 2:00 PM – 5:00 PM | 3 hrs | Short | TBD | TBD | TBD | TBD | TBD |

Once routes are selected, polylines go into the shared
`route_polyline` table (see
`5-Infra-Reference/tougecon-supabase/migrations/20260614000001_routes_route_polyline.sql`).
The drive app already has a polyline seed script at
`3-Driver-App/tougecon-drive-app/scripts/seed-route-polylines.mjs` that
can be adapted.

## Driver ↔ route matching

- Driver buys tickets for N routes via Shopify.
- Order → driver match flows through the Shopify webhook into
  `tougecon-admin-tool` (see
  `4-Admin/tougecon-admin-tool/app/shopify_routes.py`).
- Admin assigns driver to a specific pack on a specific route.
- Assignment lands in the `route_assignments` Supabase table (schema
  in `5-Infra-Reference/tougecon-supabase/migrations/20260611000001_route_assignments.sql`).
- Driver sees their pack assignment in the drive app.

## Sellout economics

- 150 cars / route × 3 routes = 450 driver-route-tickets available
  in total.
- At the all-in $185 bundle, max route revenue = 150 × $185 = **$27,750**.
- The `apnl.html` P&L models fill % with an assumed bundle mix of
  ~30% / ~45% / ~25% (1-route / 2-route / 3-route).

## Sweep & safety

- Each pack needs a sweep vehicle. Sweep driver = TBD per route.
- Hazard reporting uses the `route_hazards` table (schema in
  `5-Infra-Reference/tougecon-supabase/migrations/20260611000003_route_hazards.sql`).
- Live telemetry: `route_session_telemetry` (schema in
  `5-Infra-Reference/tougecon-supabase/migrations/20260611000002_route_session_telemetry.sql`).

## Open

- Route list (need at least 3 to support the 3-tier pricing).
- Pack size per route.
- Lead + sweep driver per route.
- Gap between packs.
- Pre-event route inspection (who, when).
