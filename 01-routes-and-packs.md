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

- **Initial car count for the event:** 20.
- That is the kickoff in-park cap, not necessarily the route cap.
- Route cap per pack: TBD. Will be set by road conditions, sweep
  vehicle, and lead driver availability.

## Route list

| # | Route name | Type | Length | Pack size | Lead driver | Hazards noted |
|---|---|---|---|---|---|---|
| 1 | TBD | TBD | TBD | TBD | TBD | TBD |
| 2 | TBD | TBD | TBD | TBD | TBD | TBD |
| 3 | TBD | TBD | TBD | TBD | TBD | TBD |
| 4 | TBD | TBD | TBD | TBD | TBD | TBD |
| 5+ | TBD | TBD | TBD | TBD | TBD | TBD |

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
