# Project status

Last updated: 2026-10-12

This file is the **single place that says where the project is right now**. It is updated at the end of every session
(see `AGENTS.md` section 6). If it disagrees with the code, one of them is wrong: find out which and fix it.

## Current phase

**R0: Planning and review.** SapienZero was created on 2026-10-12 as a new repository, spun out of the earlier AskOverlay
project (which continues separately as a small finished project). A complete plan (vision, requirements, design,
process) exists as Draft v0.1. It is **waiting for outside review**: the owner is sending the
[review brief](../REVIEW-BRIEF.md) to a reviewer. **No product code has been written yet.** The product direction is
*Proposed* in [ADR-0001](../decisions/0001-pivot-to-an-ai-test-agent.md), not yet *Accepted*.

## What exists in the repository today

Documentation and tooling only.

| Part | State | Checks (last run 2026-10-12) |
|---|---|---|
| Documentation system: `docs/`, `AGENTS.md`, `tools/check_docs.py` (31 tests, including dangling-reference detection) | Imported from the AskOverlay plan branch, renumbered and renamed; see the import commit | See the verification line in "Last session" |
| CI: `ci.yml` (ruff lint, `ci-ok` aggregate) and `docs.yml` (documentation checks) | Ran on GitHub on 2026-10-12 for the first push: both `CI` (19 s) and `Docs` (12 s) succeeded | Green on `main` at 710ef0e |
| GitHub scaffolding: issue forms, PR template, CODEOWNERS, Dependabot, `SECURITY.md`, `CONTRIBUTING.md` | Imported; paths adjusted | n/a |
| Product code, test bed, evaluation harness | **Do not exist yet** | n/a |

## Decisions in force

Proposed (under review): [ADR-0001](../decisions/0001-pivot-to-an-ai-test-agent.md) the product is an AI test agent,
ADR-0002 documentation as memory, ADR-0003 verdict computed from assertions, ADR-0004 MCP surface as plain tools,
ADR-0005 local-first with optional service mode. Nothing is Accepted yet. See the [decision log](../decisions/README.md).
The predecessor's decisions (AskOverlay ADR 0001 to 0008) stay in the `askoverlay` repository.

## Evidence we have

Only the predecessor's pointing experiment (about 85% right control, about 80% on small controls, one judge): summarised
in [predecessor evidence](../05-evaluation/predecessor-evidence.md). No measurement of the test agent exists yet.

## Exact next step

1. The owner sends [REVIEW-BRIEF](../REVIEW-BRIEF.md) to a reviewer and pastes the reply into a copy of the
   [review feedback template](../templates/review-feedback-template.md). A fresh chat is started with the
   [kickoff prompt](../handoff/kickoff-prompt.md).
2. **Triage the feedback** (accept, reject, defer; record why), apply accepted changes to the documents on a branch, and
   open a pull request. Run the independent cold-start drill ([drill log](drills.md)) with a fresh agent.
3. Merge the plan, tag `plan-v0.1`, then decide ADR-0001 to ADR-0005 (Accepted or Rejected).
4. If ADR-0001 is accepted, start **R1.0** of the [roadmap](../03-features-and-roadmap.md): the seeded-bug test bed, the
   30-test suite and the **frozen pass bar**, with **no agent code before the bar is frozen**
   (see [evaluation strategy](../05-evaluation/evaluation-strategy.md)).

## Open questions

See [open questions](../07-open-questions.md). The name is decided (SapienZero). Blocking: licence, which predecessor
pieces to reuse, the owner's weekly time budget, and which LLM provider(s) the first measurements use. The repository is
**public** (OQ-12, closed).

## Housekeeping and risks (known, not yet fixed)

- The repository is **public**, so everything committed is world-readable: never commit keys, `.env` files or private data.
  Turn on secret scanning and push protection; CodeQL and dependency review become available and are still to be added.
- The first GitHub Actions run passed (see above). Pull-request runs and branch protection are still untested.
- Repository settings (branch protection, secret scanning, environments) are **not applied**: they are manual and listed in
  the engineering handbook, section 9. Branch protection is available because the repository is public.
- Whether prompts sent through a **free-tier** Gemini key may be used by Google to improve its products is unverified
  (OQ-06); this matters before claiming that screenshots are never stored.
- Action SHA pinning is pending a tool.
- Trademark and domain checks for the name "SapienZero" are not done.

## Last session

2026-10-12: created the repository by importing the plan from the AskOverlay branch `docs/plan-v0.1` (tag
`archive/sapienzero-plan-v0.1`): dropped the predecessor's decisions 0001 to 0008, renumbered the five test-agent decisions
to ADR-0001 to ADR-0005, renamed the package to `sapienzero`, rewrote CI and Dependabot for a repository without product
code, added the predecessor-evidence page, the kickoff prompt and the review feedback template. Not copied on purpose: the
overlay application code, the evaluation harness, any private data, keys and Docker files.
Verified: see the commit message of the import for the exact checks run. **Not verified:** anything on GitHub itself and
the independent cold-start drill.
