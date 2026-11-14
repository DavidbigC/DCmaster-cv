# JD Aggregator and CV Tailoring Workflow

**My role [Mine]** — I set the sourcing, screening and tailoring requirements for my own job search and reviewed the resulting CVs. AI coding agents built the application under my direction [Directed].

**Dates** — October 2026.

**Stack [AI detail]** — Local macOS web app, Python, FastAPI, SQLite, Claude Code, Playwright.

- Aggregates crypto and Web3 jobs across roughly 640 configured sources, including 14 ATS platforms, job boards, regional feeds and Telegram. Concurrent ingestion uses per-host throttling and tracks where each canonical job was seen.
- Enriches postings with the full description and normalizes location, working arrangement, seniority and language. De-duplicates across sources while retaining provenance and ranks the shortlist by candidate fit and preferences.
- Uses a structured Claude Code handoff for fit scoring and a draft, critique and revision workflow tailored to the posting. Validates the structured output for required fields and privacy rules. The model review and my review check support for the claims.
- In the documented October backfill, 12,078 jobs were active, 96.8% had full descriptions and 99.5% had dates. In an earlier full poll, 23,686 source sightings resolved to 10,263 canonical jobs. [Operating measurements](https://github.com/DavidbigC/jd-aggregator/blob/dc8de89/ARCHITECTURE.md#operating-notes-v2-backfill-2026-10-22)
- Supports individual and batch PDF export through Playwright. The application runs locally, and the drafting workflow uses Claude Code.

[Public repository](https://github.com/DavidbigC/jd-aggregator)
