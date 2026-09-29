# Preferred stack after v0

**1. What it is.** After v0, the Steward moves to Cloudflare's Workers Paid plan (minimum $5 USD per month; developers.cloudflare.com/workers/platform/pricing/, read 2026-09-29). The team then builds on the preferred stack (`Objective.md` §3.1).

**2. Facts to carry into that decision.** Gathered 2026-09-28 and 2026-09-29 from developers.cloudflare.com:
- Python Workers run CPython compiled to WebAssembly (Pyodide). Only pure-Python packages and packages built for Pyodide work.
- "Flask is supported in Python Workers."
- No ORM is documented for Python on D1. SQLAlchemy on D1 is unverified. One unverified snippet says only its synchronous mode works.
- No beta or generally-available label was found for Python Workers.
- Containers run any language on the paid plan. Their release status is unconfirmed.
- Only JavaScript and TypeScript run on Workers without WebAssembly.
- pywrangler needs uv and Node.js.

**3. Why it waits.** It is out of v0 scope (P-5).

**4. What unblocks it.** v0 is done.
