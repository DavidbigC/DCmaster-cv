# Other 2024–2025 DeFi Tools and Research

**My role [Mine]:** built hands-on — the strategies, research questions, code and conclusions are mine.

---

## Trading and automation

- **Lighter ↔ Bluefin arbitrage / market making** (Jun–Aug 2025): Python Bluefin fill monitor + Go Lighter hedge server over TCP (sub-100 ms), long/short Bluefin market makers, Go order-book monitor, EdgeX analysers
- **Multi-venue funding monitor** (Aug 2025): Lighter / EdgeX / Bluefin / Drift / Paradex / Binance funding APR comparison server with a Telegram bot and API latency tests
- **Lighter ↔ Paradex** (Sep–Nov 2025): Go market lists and Paradex order-book WebSocket for an arb monitor
- **Bluefin + AlphaLend rate bot** (Jun 2025): TypeScript Sui bot logging funding and lending rates every 5 minutes, Telegram alerts, PM2
- **Berachain iBGT / Dolomite monitor** (Jun–Jul 2025): contract reads, Uniswap V3 pricing, LTV and liquidation price, borrow rates, funding comparison, Telegram bot commands
- **Silo vault withdrawal bot** (2025): Node bot polling vault liquidity every 3 s with 6-RPC failover, gas cap, dry-run
- **Price predictor** (2025): Bybit 1-minute data into SQLite with prediction and analysis scripts

## Data and indexing

- **Envio indexers** (2025): HyperIndex configs for BSC IDO contract events
- **Dune Sim IDX — Aave V3 listener** (Jul 2025): Solidity listener on Borrow events with Foundry tests and a Cloudflare Workers + Drizzle API ([repo](https://github.com/DavidbigC/Dune-sim))
- **Portfolio tracker** (Jan 2025): Flask + SQLAlchemy + Flask-Login multi-user position and P&L tracker, SQLite → PostgreSQL (Neon), deployed on Render

## Calculators and analysis

- **DeFi Toolbox** (Dec 2024): money-market + perp delta-neutral sizing and LP split calculators ([repo](https://github.com/DavidbigC/Defi-toolbox))
- **Dolomite tools** (Jul–Oct 2024): ARB STIP delta-neutral farming calculator; collateral auto-trading notebook using Odos swap data
- **BAYC liquidity investigation** (Sep 2024): R Markdown with Dune NFT trade SQL, Blur lending rates, floor and order-book charts ([repo](https://github.com/DavidbigC/BAYC-trading-analysis))
- **Best EVM for GameFi** (Aug 2024): DappRadar API comparison of the top 100 gaming dapps on Base, Arbitrum and Blast ([repo](https://github.com/DavidbigC/Best-Gaming-EVM))
- **Jupiter top traders** (Jul 2024): Dune client analysis ([repo](https://github.com/DavidbigC/Jupiter-best-trader))
- **Dune dashboards and writeups** (2024–2025): Contango $TANGO analysis and trading dashboard, SOFA protocol, CARV node sale, sUSDe PT APY prediction, Dolomite farming writeup

## Tags

DeFi automation · on-chain analytics · Dune · funding monitoring · Go · TypeScript · Python
