# Perpl Funding, Market Microstructure and Strategy Research

**My role [Mine]** — I chose the questions, set the execution and risk assumptions, decided which signals to arm, and used the results to change quoting, hedging and funding decisions. AI agents collected data, built replays and performed the analyses under my direction [Directed].

**Dates** — July–November 2026.

## Funding economics and forecast validation [Directed]

- Reconstructed 161 days of Perpl–Lighter funding history from venue data and checked the overlapping epochs against the live capture. Normalized rates using observed interval lengths and separated periods with different Perpl funding clamps.
- Revisited a 15-day sample that sat inside a favorable regime. Longer history showed that static long-Perpl carry averaged approximately −1.3% annualized. Causal regime-following simulations with switching costs returned +5–6.5% annualized, and all 24 tested parameter combinations were positive in the walk-forward holdout.
- Compared funding settlement direction with the sign of average carry during a holding window. A September validation used non-overlapping windows. Six-hour average-carry direction scored 78.4% in the latest clamp era, including the same point estimate across 37 holdout windows. Single-epoch direction was about 66%.
- Found that a fixed dead band lost selectivity after a funding-clamp change. Tested a trailing quantile with a fixed-band fallback for short histories. The adaptive band kept the share of periods that passed the filter within 73–79% across three clamp eras and shipped disabled by default.
- Tested the tendency for rates to dip toward zero and return, distinguishing the venue's funding premium from the cross-venue basis the engine trades. Rechecked the results by clamp era, hold duration and signal half-life. In a separate lead–lag study, the tested oracle references lagged the book.
- Recovered 47,294 minute buckets spanning a 32.9-day carry flip. Replayed basis-only, carry-only and blended quote-side signals on identical data with switching costs and block-bootstrap checks. At the observed hold time, the blend returned 0.195 bps/hour versus 0.081 for the basis-only comparator in simulation. The selected blend was already armed when the live setup was verified.
- Backtested a separate BTC/ETH funding-hold rule. In one 62.75-day sample it produced nine positive holdings from nine and +3.44 bps/day net in simulation. I chose to ship the later six-hour forecast and regime display as operator information.

## Execution and market selection [Directed]

- Measured queue position, competing makers' fill behavior, stale-quote rates, spread capture and hedge giveback with Monad data. The decomposition helped identify where the apparent Perpl-leg edge leaked after hedging.
- Compared fee-adjusted maker and taker entries, session and weekday effects, spread and expected cost across symbols, and the economics of the SOL pilot.
- Measured Binance-to-Lighter lead–lag at roughly 200–300 ms in one study. Compared market displacement, order-book imbalance and change detection, and tested whether quote widening and volatility-based resizing helped during fast moves.
- Tested a volatility size ramp that retained 77% of volume while reducing negative entry edge by about two-thirds in the studied sample. Used 1/5/30-second markouts to distinguish being run over during price moves from persistent post-fill toxicity.
- Timed the order and hedge path across local and Tokyo infrastructure using paired feed captures, gateway pings and acknowledgement traces. Evaluated event-driven quoting against the persistent order-message budget.
- In the November BTC pick-off follow-up, classified 3,426 fills by detection, order-ID resolution, spend caps and race outcome. Lost races after a cancel was sent accounted for 61% of the measured stale-quote loss. Separated jumps from gradual moves and compared their detection and block-inclusion time. [On-chain transaction-ordering study](perpl-onchain-execution.md)

[Perpl market maker](perpl-mm.md) · [Monad data and L3 book](perpl-indexer.md) · [Cross-venue research library](research-library.md)
