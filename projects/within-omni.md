# Within-Omni — RWA Future vs Swap Pair Trading

**My role [Mine]:** I set the two-rate model (30 s while gathering, 1 s only while trading), ruled that the swap leg goes first with the perp 50–300 ms behind, sized the pairs, and decide when to press Start. My observation that oil pair spreads widened in steps started the basis research. AI agents built the monitor and executor [Directed].

**Type:** monitor and paired executor for economically equivalent instruments on one venue
**Dates:** September–November 2026
**Stack:** Python, Flask, curl_cffi, SQLite

---

- monitors the executable spread between Omni's RWA perpetual futures and their swap twins (gold, silver, copper, US500, WTI, Brent); pairs discovered from venue metadata, declared pairs where naming conventions break
- per-pair cadence cut order-endpoint traffic from 86/min to 8/min; closed-market backoff cut refused probes from 160/hr to ~4/hr
- paired executor: three consecutive threshold confirmations, global execution slot held through repair, swap-first ordering, one-sided fill compensation, two-read reconciliation, force-stop and alert on ambiguity
- positions panel, trade-history integration, EW rails, per-pair health gating; backwardation page with the oil forward curve and the next roll's cost
- oil basis research: the 4-hourly spread widening is the perp's funding; the uncompensated risk is a 60–94 bps index divergence between two Brent series

## November follow-through [Directed]

- Compared quoted paired spread with actual executions across more than 900 copper, silver and gold fills. Used the measured gap and timing to tune per-leg quote synchronization and add recheck timing. Added venue-attributed realized P&L on paired fills.
- Added handling for pending swap-financing publications and surfaced the last applied rate. Renewed multiple Omni account sessions in place, while bounding the HTTP connection pool and closing stale sessions after rotation.
- Tracked the copper perp–swap spread across different futures-roll weights and financing calendars, with the spread decomposed into the index gap and each leg’s premium. [Copper research](market-data-research-tools.md#copper-perpetual-versus-swap-research-directed)

## Tags

relative value · RWA perps · commodities · execution safety
