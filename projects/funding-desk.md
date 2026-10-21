# Funding & Spread Arbitrage Desk

**My role [Mine]:** my core trading business. I pick which pairs to hold and in which direction, size them, run the manual and automated executors, move capital between venues, and decide what to cut. The attribution analysis below was run by AI agents on my P&L data; the decisions are mine. The tooling is AI-built to my spec [Directed].

**Type:** delta-neutral cross-venue funding-carry and spread arbitrage across crypto perps, RWAs and tokenised equities
**Venues:** Omni / Variational ↔ Lighter ↔ trade.xyz
**Dates:** 2026-01 → ongoing

---

## What the attribution showed (42-day window, May–Jul 2026)

- ~78% of explained P&L came from funding (Lighter 68%, Omni 10%) and ~21% from spread capture; the attribution reconciled to equity change within ~3.5%
- 13,114 trades; spread capture averaged +3.07 bps — the spread is the toll paid to enter funding positions, not the product
- best pairs were high-carry crypto names (NEAR, ZEC, LIT, WLD, FIL, ZRO, ADA) plus CL/WTI; a gold pair was churning large notional for ~0 bps and paying funding both ways → kill list
- spread P&L positive 10–20 UTC, negative 0–5 UTC and on Mondays / Saturdays → clock gating
- basis does not drift into funding settlements — no free "settlement sniping"

## Desk tooling [Directed]

- /trading executor: up to 4 concurrent sessions, parallel legs, hedge venue switchable between Lighter and trade.xyz, WS-verified execution prices, capacity warning before Omni rejects on OI/skew caps
- /arbitrage scanner: funding and spread across 80+ pairs with an RWA tier, settled-funding history, live prices, Telegram alerts
- /historical-data: settled-funding stats via boundary sampling, index-vs-mark premium chart, market-hours filter
- funding ledger: every funding payment backfilled (1,803 Omni + 12,795 Lighter rows), daily sync, daily funding chart; cashflow ledger so deposits never read as profit
- unified three-venue portfolio with net delta per symbol

## Research behind it

- 135-symbol, 6-month spread-vs-funding screen: tier-1 harvest picks paid >20% APR funding difference with ≥80% sign persistence and recovered round-trip cost in <5 days
- carry screen = mean |funding diff| ÷ (1 + entry cost) × sign persistence
- CL ↔ WTI funding regime: +17.5%/yr carry, Lighter ~9 bps structurally rich

## Tags

funding-rate arbitrage · delta-neutral carry · P&L attribution · portfolio management · live capital
