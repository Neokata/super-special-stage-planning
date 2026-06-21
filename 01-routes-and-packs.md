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

- **Route cap per slot** (set 2026-06-21):
  - Friday morning (long, 6 hrs): **60 cars** at **$150/car**
  - Saturday morning (short, 5 hrs): **150 cars** at **$75/car**
  - Saturday afternoon (short, 3 hrs): **150 cars** at **$75/car**
- **Total route-ticket ceiling: 60 + 150 + 150 = 360 driver-tickets.**
- **Max potential route revenue at 100% sellout: $9,000 + $11,250 +
  $11,250 = $31,500.** (Down from the old $58k ceiling that assumed
  everyone bought the all-in $185 bundle.)
- **No discounts.** Each slot is a single price. A driver taking all
  3 slots pays $300 ($150 + $75 + $75).
- **No stepped pricing.** Replaces the old $75/$60/$50 tier model
  that was based on multi-route bundles.

## Pack model

- **Friday:** 2 packs of 30 cars, 2 lead drivers + 2 sweep drivers.
  Each lead/sweep driver works the Friday long route only. **4
  driver-pays for Friday.**
- **Saturday:** 5 different physical routes, each run twice (Pack A
  in the morning session, Pack B in the afternoon session). Per
  route: 1 lead + 1 tail/sweep driver. **Per route: 2 staff drivers.**
  Same lead/tail team runs both sessions of their route (AM then PM),
  so it's one pay per staff per day, not per session. **5 routes × 2
  staff = 10 driver-pays for Saturday.**
- **Total weekend staff drivers: 4 (Fri) + 10 (Sat) = 14.**
- **Per-pack: 15 cars, 1 lead, 1 tail.** Each pack has 15 cars
  regardless of which route.
- The "Pack A / Pack B" distinction is a timing offset (AM session vs
  PM session) on the *same* physical route — not different routes.
- **150 cars/session = 10 packs × 15 cars.** Per Saturday day (AM + PM
  combined): 300 cars total across all 5 routes. **Per Saturday
  session: 150 cars.**

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

## Route list

| # | Day | Time (CT) | Duration | Cap | Price | Pack model | Routes (different roads) | Name | Length | Lead | Sweep | Hazards |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Fri Oct 2 | 10:00 AM – 4:00 PM | 6 hrs | 60 | $150 | 2×30, 2 lead + 2 sweep | 1 | TBD | TBD | TBD | TBD | TBD |
| 2 | Sat Oct 3 | 8:00 AM – 1:00 PM | 5 hrs | 150 | $75 | 5 routes × 2 packs (A+B) of 15, 10 lead + 10 sweep | 5 | TBD | TBD | TBD | TBD | TBD |
| 3 | Sat Oct 3 | 2:00 PM – 5:00 PM | 3 hrs | 150 | $75 | Same staff as Route 2, just Pack B vs Pack A timing | 5 | TBD | TBD | TBD | TBD | TBD |

**Saturday route count: 5 different physical routes.** Each route
runs twice — Pack A in the AM session, Pack B in the PM session. Same
lead/sweep team per route works both sessions.

**Saturday staff:** 5 routes × (1 lead + 1 tail) = 10 staff drivers
working both sessions. Saturday pack size: 15 cars.

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
