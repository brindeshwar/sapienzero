# Open questions

Status: living document. Anything we do not yet know or have not yet decided that could change the work. Each has an
owner, a "needed by" point, and a default we will use if nobody decides. When answered, move the answer into the right
document (an ADR if it is a decision), mark the row *Closed*, and keep the row for history.

| ID | Question | Why it matters | Options and leaning | Decides | Needed by | Status |
|---|---|---|---|---|---|---|
| OQ-01 | **Product name.** The predecessor's name "AskOverlay" described an overlay that no longer exists | Public name, package and command names, domain, repository | **Provisional: SapienZero**, used so far for the repository, the package and the command (`sapienzero`). The owner will confirm or change it and the answer is recorded here. Before anything is published: trademark and domain checks (not done) | Owner | Confirm now; trademark and domain check before the first public release | Open (provisional name in use) |
| OQ-02 | **Licence** | Determines who may use, copy and contribute; matters for the portfolio | Permissive (MIT or Apache-2.0) leaning Apache-2.0 for the patent grant; copyleft only with a reason | Owner | Before the first public release | Open |
| OQ-03 | **Which pieces of the predecessor's code to reuse, and how** (model access with fallback, error classification, evaluation tooling). The overlay code itself stays in the `askoverlay` repository | Avoid copying large untested code; keep provenance | Leaning: re-implement small pieces test-first, record the source commit in the pull request; no wholesale copy | Owner | R1.0 | Open |
| OQ-04 | **Weekly time budget and target dates** | The roadmap has effort, not dates | Owner states hours per week; planning converts effort to calendar with a stated margin | Owner | R0 exit | Open |
| OQ-05 | **Which model provider(s) and budget** for the first measurements | Latency, cost and quota decide what R1 can show; free tiers are slow and rate-limited | Leaning: current Gemini lite models first (already integrated), a paid tier for the final bar run; keep the gateway provider-neutral | Owner | R1.0 | Open |
| OQ-06 | **Do prompts sent with a free-tier Gemini key get used by Google to improve its products?** | Privacy claims for any screenshots or page text; the security model assumes the provider sees them | Verify in the provider's current terms; until verified, claim nothing and prefer a paid tier for sensitive material | Owner (with a reviewer) | Before any privacy statement is published | Open |
| OQ-07 | **Who reviews, and how** | A solo project has no second reviewer; security-relevant changes need one | A named friend or mentor reviews security, policy and interface changes; an independent AI pass for the rest | Owner | R0 exit | Open |
| OQ-08 | **Browsers beyond Chromium** | Real users use more than Chromium | Chromium only for R1; Firefox and WebKit at R3 or later | Owner | R3 | Open (default set) |
| OQ-09 | **Test-file format** | Authoring comfort versus parsing simplicity | YAML for R1; Markdown with front matter later if wanted | Owner | R1.0 | Open (default set) |
| OQ-10 | **Python project tooling** (pip versus uv; lock files) | Reproducibility and CI speed | Spike at R1.0; choose one, record in an ADR | Owner with agent | R1.0 | Open |
| OQ-11 | **Where documentation is published** | Readability for outsiders | The repository on GitHub is enough for R1; consider static site generation later | Owner | R2 | Open (deferred) |
| OQ-12 | **Public or private repository, and history audit** | The repository may be shown to employers; history must hold no secrets | **Currently public** (the owner agreed on 2026-10-12; the owner will confirm the final answer and it is recorded here). The history is fresh (no predecessor history imported) and a secret scan of the tree found nothing before the first push. Either way: GitHub secret scanning and push protection on, and never put real keys, `.env` files or private data in a commit. The repository can be made private again | Owner | Confirm now | Open (currently public) |
| OQ-13 | **Technology of the test-bed web store** | It must resemble real sites: some server-rendered pages and some JavaScript-heavy ones | Leaning: a small FastAPI app with templates plus a few client-side pages; decide at R1.0 | Owner with agent | R1.0 | Open |
| OQ-14 | **Authentication flows with verification codes** | Real applications use them; they must not be automated carelessly | Out of scope for R1; later: approved test accounts and test-mode bypasses, never real inboxes | Owner | R3 or later | Open (default set) |
| OQ-15 | **Retention of the earlier evaluation data** (screenshots, labels, judgments) | Private data; needed only to regenerate or re-audit results | Keep a private encrypted backup outside the repository, or delete once the aggregates are recorded | Owner | R0 exit | Open |

Questions the owner asked to defer: all of the above were raised in review and intentionally **not** blocking the plan; they are
resolved at their "needed by" point.
