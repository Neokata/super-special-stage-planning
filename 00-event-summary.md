# 00 — Event summary

One-page brief for the Super Special Stage event. Anyone reading this
file should be able to summarize the event in five sentences.

## What

A two-day, multi-route, **pace-car-led road tour event**. Drivers
register for one or more curated routes; on event day, packs of cars
are led by a staff driver through each route in sequence. Friday night
is a separate kickoff event in a park (see `03-friday-kickoff.md`).

## When

| Day | Start | End | Notes |
|---|---|---|---|
| Friday Oct 2, 2026 | Morning (TBD exact time) | End of day driving | Packs run continuous |
| Friday Oct 2, 2026 | 6:00 PM CT | 9:00 PM CT | Friday kickoff event |
| Saturday Oct 3, 2026 | Morning (TBD) | End of day | Final packs complete |

All times Central.

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

See `06-open-questions.md`. Top three right now:

1. Exact route list and pack size per route.
2. Friday kickoff event name (cannot reuse "TougeCon Underground" per
   root `AGENTS.md` naming rule).
3. Friday morning start time and pack cadence.
