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
  This is heavier per-car staffing than Saturday because Friday is the
  long route (6 hrs) and the smaller pack size means each lead/sweep
  pair is responsible for only 30 cars.
- **Saturday morning + afternoon:** Pack size TBD. With 150 cars per
  slot, options are:
  - 5 packs of 30 (5 leads + 5 sweeps = 10 staff drivers for Sat AM,
    10 for Sat PM, 20 total)
  - 10 packs of 15 (more staff, smaller packs)
  - 6 packs of 25 (middle ground)
  - 3 packs of 50 (large packs, fewer staff, harder to manage)
- Pack decision impacts cost significantly — more packs = more
  per-pack staffing (gas, meals, comms) but easier route management.
  See `04-operations.md` and `05-budget.md` once the Sat pack size
  is picked.

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

| # | Day | Time (CT) | Duration | Cap | Price | Pack model | Name | Length | Lead | Sweep | Hazards |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Fri Oct 2 | 10:00 AM – 4:00 PM | 6 hrs | 60 | $150 | 2×30, 2 lead + 2 sweep | TBD | TBD | TBD | TBD | TBD |
| 2 | Sat Oct 3 | 8:00 AM – 1:00 PM | 5 hrs | 150 | $75 | TBD | TBD | TBD | TBD | TBD | TBD |
| 3 | Sat Oct 3 | 2:00 PM – 5:00 PM | 3 hrs | 150 | $75 | TBD | TBD | TBD | TBD | TBD | TBD |

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
