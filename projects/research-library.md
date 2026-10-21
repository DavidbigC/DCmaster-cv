# Cross-Venue Research Library (May → Oct 2026)

**My role [Mine]:** I asked the questions and made the trading decisions from the answers; AI agents pulled the data, ran the analysis and wrote the reports [Directed]. Data came from the platform's own snapshot tables (hundreds of thousands of 1-minute rows) plus venue docs and APIs.

---

- **RWA arbitrage findings:** 31 symbols, ~132k snapshots; tiered universe by edge vs round-trip cost, mean reversion and liquidity — gold cleared 2× cost 86% of the time; persistent wide gaps (Korean ADRs, AMD, MU, ORCL) classified as carry, not arbitrage
- **Funding mechanisms, trade.xyz vs Lighter:** formula-level comparison; funding moves with the arb for metals and most equities, against it for WTI/Brent and persistent-gap names
- **Oracle and index risk:** Lighter (Chainlink / Pyth / Stork per asset) vs trade.xyz (in-house relayer, per-update clamp, futures-roll blends); per-asset-class risk map explaining 44–55% funding misalignment on energy
- **HIP-3 landscape and pair map:** Hyperliquid's 9 perp-DEX slots; 28 viable trade.xyz ↔ Lighter RWA pairs; underlying-alignment check (copper futures vs spot flagged)
- **Autonomous MM edge thresholds:** starting thresholds from 154,758 snapshots
- **Taker-only synthesis:** explicit round-trip cost model that showed earlier dashboard $/day figures were too optimistic; universe ranked by envelope ÷ cost (WTI 8.5×, Brent 5.8×, gold 5.6×)
- **WTI playbook:** basis half-life 13.1 min; funding capture lost money at every hold from 2 h to 48 h, so trade the basis; maker / taker / escalating-maker backtests (escalating maker 9.03 bps net per cycle)
- **RWA spread + funding synthesis:** 31 pairs, walk-forward with fees
- **135-symbol funding-harvest screen:** 6 months of crypto data, ranked by funding edge, sign persistence and breakeven days
- **Oil roll weekends:** 248,724 snapshots across three venues; deep negative roll funding fades over the weekend and returns with the roll on trading days
- **Oil perp vs swap:** futures-curve backwardation as the economic explanation; swap financing charged in points, not percent
- **Within-Omni oil basis:** spread decomposed into a perp discount that resets at session reopen plus a 60–94 bps uncompensated index divergence
- **Oracle → basis predictability (Perpl):** no — every reference series lags the book
- **Funding regimes:** 161 days; regime-following +5–6.5%/yr vs −1.3%/yr static, all 24 parameter sets positive out-of-sample
- **Funding prediction validation:** direction right 78% at 6 h on non-overlapping windows; never pool across venue clamp eras
- **Adaptive dead band:** a fixed band armed 41% / 69% / 94% across three clamp eras; a quantile band holds 73–79%
- **Basis + carry blend:** validated on 32.9 days straddling a carry flip (bootstrap P = 100% in both regimes), then run live
- **Funding hold strategy (BTC + ETH):** in backtest won 9 of 9 trades over 62.75 days, +3.44 bps/day net; shipped as a read-only dashboard line by my choice
- **Market-maker studies:** competitor benchmarking from chain data, session profiling, regime detection, Binance → Lighter lead-lag, run-over vs adverse selection (see `perpl-mm.md`)
- **Arb studies:** slip decomposition, spike adverse selection, regime tradeability (see `lighter-arb.md`)
- **Other:** delta-hedged LP simulation, DEX contract review, Omni oil swap structure analysis

## Tags

quantitative research · market microstructure · funding and basis analysis · research-to-decision
