# Treasury, Rebalancer and Liquidation-Risk Stack

**My role [Mine]:** I wanted capital to move between venues automatically when one side gets close to liquidation, required liquidation monitoring and de-risking after real drawdowns, set alert behaviour and thresholds, decide when each guard is armed, and mandated that money-moving code never reaches any server or remote. AI agents built and hardened it [Directed].

**Dates:** 2026-05 → 2026-10
**Stack:** Python, web3, Textual TUI, Arbitrum USDC, CCTP, Telegram

---

## Treasury and rebalancer (local only)

- deposit / withdraw primitives for Lighter (fast withdraw, CCTP deposit) and Omni (withdrawal, relayer deposit) — all four legs proven with small real-money round trips
- rebalancer: triggers when any venue's closest position is <10% from liquidation, equalises equity to a 5% band in fixed units, donor keeps a free-margin floor; Textual control-hub TUI
- money safety: dry-run default, max-amount cap, prechecks before submit, no retry on money-moving calls, typed confirmation for live mode; kept off every remote by a pre-push hook; 160 tests

## Liquidation-risk stack

- liquidation alarm bot: all positions on three venues, 5-tier distance ladder with a velocity bump and hysteresis, on a separate Telegram bot from routine alerts
- auto-deleverage design: reduce both legs of a hedged pair until distance is back above 10%
- liquidation guard: % adverse move until liquidation as the operator unit, exposure netted only within an underlying, urgency from position ÷ daily volume; deployed observe-only by my choice
- per-coin guards on the cross-deployment arb; capacity warning before a venue rejects an order on OI / skew caps

## Tags

treasury operations · on-chain transfers · risk management · alerting · production safety
