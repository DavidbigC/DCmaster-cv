# Treasury, Prediction-Market and On-Chain Research Tools

**My role [Mine]** — I chose which markets and protocols to investigate, specified the questions and constraints, and interpreted the outputs. AI coding agents built the 2026 tools and ran analyses under my direction [Directed].

## SEC EDGAR 13F institutional positioning [Directed]

- Directed a local pipeline and read-only dashboard for institutional positioning in U.S. Treasury ETFs. Preserved filing versions and amendments, separated comparable filers from changes in coverage, and added manager drill-downs.
- Parsed 2.54 million holding rows from 42 managers covering Q1 2025 through Q1 2026. The data contained 216 filed versions and 204 after amendment deduplication.
- Compared reported ETF share flows, manager breadth and long-duration put and call positions. The measures are delayed positioning indicators for the reported securities.

## IBKR U.S. Treasury dashboard [Directed]

- Directed a local market monitor for Treasury bills and bonds, with public IBKR quotes, dated official-source fallbacks, cost-adjusted yield comparisons and historical Treasury yield curves back to 1990.
- Added local persistence, source and freshness indicators, and optional read-only IB Gateway access. The reviewed store contained about 176,000 broker quote rows and 100,000 official curve observations. A repository study compared date-aligned yields across 403 bonds and found roughly 90% of Treasury-list estimates within 3 bps of the IBKR ask yield. The market view was built. Account holdings and execution views were scoped in the design.

## HIP-4 prediction markets and Lighter comparisons [Directed]

- Directed a Rust monitor for comparing short-dated HIP-4 outcomes with reference markets. Added quarter-hour pair discovery, explicit strike and settlement-source comparison, fee- and depth-adjusted executable prices, and capture and replay.
- In a short matched-feed trial, the fast feed exposed more book updates. A separate comparison found zero median receive-time lead for racing sockets.
- Built a separate catalog view across deployers, covering contract metadata and definitions, related strikes, fee schedules and incentive coverage. Captured depth and official resolutions for later analysis.

## Papertrade protocol and launch research [Directed]

- Directed a read-only data pipeline and dashboard for a Hyperliquid ecosystem protocol. Collected contract state via HyperEVM Multicall3 and incremental logs, replayed stored events on restart, and investigated depositor histories using HyperCore data.
- Tracked positions, payouts, minting and burning, liquidity and depositor behavior. Local records included about 1.07 million events and 27,700 state snapshots.
- Modeled fee distribution, payout queues, and staking scenarios with historical BTC/ETH paths and Monte Carlo simulations.

## Copper perpetual versus swap research [Directed]

- Compared the financing and roll economics of Omni’s copper perpetual and copper swap. Aligned the dated futures and their roll weights, decomposed the spread into index divergence and each instrument’s premium, and tracked the next scheduled roll checkpoints.
- Compared realized spreads with the schedule-implied spread and included Binance copper funding as a benchmark. [Within-Omni paired execution](within-omni.md)
