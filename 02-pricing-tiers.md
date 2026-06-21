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

## Open

- **Spectator question:** Is driving-in the only way to attend the
  Friday kickoff, or can walking-in spectators attend for free?
  Currently reads as: drive-in = $50 (or $30 reserved), walk-in = free.
  Confirm.
- **Shopify product structure:** One SKU per route? A bundle SKU? Or
  a single "build your pack" product with custom line items? Need to
  decide before the store is set up.
- **Refund policy** if a route is cancelled (weather, hazard, etc.).
- **Raffle / prize ticket sales:** Separate from parking? Sold at
  the gate? Online pre-sale? See `03-friday-kickoff.md`.
- **Is the kickoff parking a separate Shopify product, or sold at
  the gate (cash / Square)?** TBD.
