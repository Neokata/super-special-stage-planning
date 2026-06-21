# 02 — Pricing tiers

## Driver tickets (per slot, no discounts)

| Slot | Day | Time (CT) | Duration | Cap | Price | Notes |
|---|---|---|---|---|---|---|
| Route 1 (long) | Fri Oct 2 | 10:00 AM – 4:00 PM | 6 hrs | 60 cars | **$150** | Premium slot: long route, small pack (2×30) |
| Route 2 (short) | Sat Oct 3 | 8:00 AM – 1:00 PM | 5 hrs | 150 cars | **$75** | Morning pack |
| Route 3 (short) | Sat Oct 3 | 2:00 PM – 5:00 PM | 3 hrs | 150 cars | **$75** | Afternoon pack |

**No discounts.** Each slot is a single price. A driver taking all 3
slots pays $150 + $75 + $75 = $300 for the full weekend.

**Max potential route revenue at 100% sellout:**
- Route 1: 60 × $150 = $9,000
- Route 2: 150 × $75 = $11,250
- Route 3: 150 × $75 = $11,250
- **Total: $31,500**

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

Shopify product structure: 3 separate SKUs, one per slot. Drivers can
buy 1, 2, or all 3 SKUs in a single Shopify cart.

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

## Open

- Refund policy for cancelled routes (weather, hazard, etc.).
- Raffle / prize ticket sales: cash/Square at the gate (per the
  spectator-policy decision above).
- Saturday pack size TBD (5×30, 10×15, 6×25, 3×50, or other).
