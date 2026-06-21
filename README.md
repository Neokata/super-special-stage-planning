# super-special-stage-planning

Planning, budgeting, and admin-side prep for the **Super Special Stage**
event. Living docs live here; built artifacts (website, check-in,
dashboard, etc.) get split out as sibling folders as they take shape.

## Status

**Pre-build.** No code yet. This folder holds event decisions, budgets,
vendor quotes, run-of-show, and similar planning artifacts only.

## Event at a glance

- **Format:** Multi-day pace-car-led road tours, packs of cars follow
  a staff driver on curated technical and scenic routes.
- **Dates:** Friday Oct 2, 2026 (morning start) – Saturday Oct 3, 2026
  (end of day). All times Central.
- **Friday night:** Kickoff event in a park, 6:00–9:00 PM CT.
- **Pricing:** $75 / $60 / $50+ per-route stepped discount.
- **Parking (Friday):** $50 in-park, $30 reserved front lot (40 spaces),
  free at Tyson Foods lot + city parking.
- **Heritage:** Same format as prior TougeCon Summer Special Stages
  (e.g. TCSS 2026). See `5-Infra-Reference/tougecon-supabase/` for the
  shared schema this event will plug into.

See `00-event-summary.md` for the full one-pager.

## Documents in this folder

| File | What it covers |
|---|---|
| `00-event-summary.md` | One-page: what / when / where / scale / format |
| `01-routes-and-packs.md` | Route tiers, pack structure, capacity per pack |
| `02-pricing-tiers.md` | $75/$60/$50+ route pricing, Shopify flow, parking tiers |
| `03-friday-kickoff.md` | 6–9 PM CT kickoff: vendors, parking, raffle, schedule |
| `04-operations.md` | Run-of-show, staffing, permits, insurance, vendors |
| `05-budget.md` | Revenue + cost, what's known vs. open |
| `06-open-questions.md` | Everything still to be decided |

## Related artifacts

| Role | Location |
|---|---|
| This folder (planning, budget, admin prep) | `4-Admin/super-special-stage-planning/` |
| Public landing page (stub) | `1-Website/super-special-stage-landing/` |
| Venue proposal (Springdale) | `1-Website/springdale-proposal/` |
| Shared Supabase schema | `5-Infra-Reference/tougecon-supabase/` |
| Past event check-in (reference) | `4-Admin/summer-stage-check-in/` |
| Past event dashboard (reference) | `4-Admin/summer-stage-admin-dashboard/` |

As the event takes shape, sibling folders will be created alongside this
one following the `summer-stage-*` convention (one folder per artifact).
Do not put code in this folder — split it out when ready.

## Conventions

Inherits all rules from `../../../AGENTS.md` (the TougeCon root).
New artifacts scaffolded from this planning should follow the
per-bucket conventions already established by `summer-stage-admin-dashboard/`
and `summer-stage-check-in/`.
