# Configuration step

**1. What it is.** The configuration step was dropped from v0. A deploy step reads the Steward's structured YAML in `2-APP/config/`, grouped by resource, then kind, then environment. It hands Cloudflare one environment's values. Plain values go as Wrangler variables. Secret values go as Cloudflare secrets (`wrangler secret put`). Locally, the step writes `.dev.vars`, which is gitignored.

**2. How the code sees it.** The code reads configuration only from what Cloudflare hands the Worker. D1 is attached per environment by a binding, not by a connection string. See Library note `Reference/Layer_Encapsulation.md` §4.9.

**3. Origin.** The Steward, 2026-09-28:

> we will need to adapt to CF's protocol for secret caching. Locally and hosted

**4. Why it waits.** v0 has no app secrets (P-6, P-7).

**5. What unblocks it.** The first secret the app needs, or V1.
