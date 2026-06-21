# 02 — Pricing tiers

## Driver tickets (per route, stepped discount)

| Route # | Price | Cumulative (if bought together) |
|---|---|---|
| Route 1 | $75 | $75 |
| Route 2 | $60 | $135 |
| Route 3 | $50 | $185 |
| Route 4 | $50 | $235 |
| Route 5+ | $50 each | +$50 each |

Sale channel: **Shopify** (per `TougeCon/AGENTS.md` — TCSS26 used
Shopify, and the Supabase `tickets` table was dropped on 2026-06-11
in migration `20260611000006_drop_tickets_table.sql`).

## Order flow

```
Shopify checkout
  → Shopify webhook
  → 4-Admin/tougecon-admin-tool (app/shopify_routes.py)
  → Supabase route_assignments table (after admin assigns pack)
  → Driver sees assignment in 3-Driver-App/tougecon-drive-app
```

No new schema is required for SSS ticket sales. The Shopify integration
and `route_assignments` table already exist from TCSS26.

## Friday kickoff parking

| Lot | Price | Spaces | Notes |
|---|---|---|---|
| In-park (kickoff venue) | $50 / car | 20 | Limited to 20 cars |
| Reserved front lot | $30 / car | 40 | Adjacent to park, dedicated |
| Tyson Foods lot | Free | TBD | Main overflow |
| City parking | Free | TBD | Remainder |

**Maximum kickoff parking revenue (paid lots only):**
20 × $50 + 40 × $30 = $1,000 + $1,200 = **$2,200**

## Spectator policy (resolved)

- **Walk-in spectators at the Friday kickoff are free.** We don't
  try to count them — too much overhead, low signal. The $50/$30
  parking charges are for *vehicles* that drive in.
- This means we will NOT be able to give an exact headcount for the
  kickoff. If marketing needs a number for permits or fire code, use
  a reasonable estimate (e.g. 2.5x paid-park count) and label it as
  such.
- Implication: raffle / merch sales at the kickoff are cash/Square
  only, no pre-sale inventory reconciliation needed.
