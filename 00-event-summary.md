# 00 — Event summary

One-page brief for the Super Special Stage event. Anyone reading this
file should be able to summarize the event in five sentences.

## What

A two-day, multi-route, **pace-car-led road tour event**. Drivers
register for one or more curated routes; on event day, packs of cars
are led by a staff driver through each route in sequence. Friday night
is a separate kickoff event in a park (see `03-friday-kickoff.md`).

## When

| Day | Start | End | Block | Notes |
|---|---|---|---|---|
| Friday Oct 2, 2026 | 10:00 AM CT | 4:00 PM CT | Route 1 (long, 6 hrs) | One continuous pack run |
| Friday Oct 2, 2026 | 6:00 PM CT | 9:00 PM CT | Friday kickoff | Park, vendors, raffle |
| Saturday Oct 3, 2026 | 8:00 AM CT | 1:00 PM CT | Route 2 (short) | Morning pack |
| Saturday Oct 3, 2026 | 2:00 PM CT | 5:00 PM CT | Route 3 (short) | Afternoon pack |
| Saturday Oct 3, 2026 | Evening (TBD) | TBD | Dinner send-off | Format TBD |

All times Central. Saturday is a 2-route day (morning + afternoon)
flanking a 1-hour break from 1:00–2:00 PM for lunch / reset.

## Where

- **Routes:** Curated technical + scenic routes, TBD. See
  `01-routes-and-packs.md` once route selection is finalized.
- **Friday kickoff:** A park in Springdale, AR. Parking breakdown in
  `03-friday-kickoff.md`.
- **Venue proposal:** See `1-Website/springdale-proposal/` for the
  Springdale pitch site.

## Scale (initial)

- **Initial car count:** 20 in-park on Friday night; route capacity
  per pack TBD.
- **Growth posture:** Add capacity as demand warrants; ticket structure
  supports multi-day, multi-route drivers.

## Format (vs. prior events)

Same format as prior TougeCon Summer Special Stages (TCSS). Reuses:

- Shopify for ticket sales (no `tickets` table — see root `AGENTS.md`).
- `route_assignments` table for driver ↔ route matching.
- `route_session_telemetry` for live route data.
- `route_hazards` for hazard reporting.
- `route_polyline` for map data.

See `5-Infra-Reference/tougecon-supabase/migrations/` for the canonical
SQL.

## Pricing snapshot

| Item | Price |
|---|---|
| Route 1 | $75 |
| Route 2 | $60 |
| Route 3+ | $50 each |
| Friday kickoff in-park parking | $50 / car |
| Friday kickoff reserved lot | $30 / car (40 spaces) |
| Tyson Foods lot | Free |
| City parking | Free |

Full pricing in `02-pricing-tiers.md`.

## Decisions still open

See `06-open-questions.md`. Top blockers right now:

1. Route list (still TBD — we have 3 slots and a 3-tier pricing
   matrix, need to pick the actual routes).
2. Friday kickoff event name (cannot reuse "TougeCon Underground" per
   root `AGENTS.md` naming rule).

## Brand vs. admin entity

- **Event brand:** TougeCon. Use "TougeCon Super Special Stage" or
  "TougeCon SSS" in marketing copy.
- **Admin / accounting / repo / vendor contracts:** Neokata. The repo
  is `Neokata/super-special-stage-planning`. Vendor invoices are paid
  by Neokata.

The owner controls both entities, so the practical effect is: contracts
and expenses route through Neokata; brand and customer-facing copy
routes through TougeCon. Do not mix the two in a single document —
vendor agreements say Neokata, marketing says TougeCon.
