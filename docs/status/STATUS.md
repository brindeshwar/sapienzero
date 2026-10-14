# Project status

Last updated: 2026-10-15

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
| CI: `ci.yml` (ruff lint, `ci-ok` aggregate) and `docs.yml` (documentation checks) | Ran on GitHub on 2026-10-12 for the first push: both `CI` (19 s) and `Docs` (12 s) succeeded | Green on `main` and on pull requests 1 to 4 (checked 2026-10-15) |
| GitHub scaffolding: issue forms, PR template, CODEOWNERS, Dependabot, `SECURITY.md`, `CONTRIBUTING.md` | Imported; paths adjusted | n/a |
| Product code, test bed, evaluation harness | **Do not exist yet** | n/a |

## Decisions (none accepted yet)

No decision is in force yet. Proposed (under review): [ADR-0001](../decisions/0001-pivot-to-an-ai-test-agent.md) the product is an AI test agent,
ADR-0002 documentation as memory, ADR-0003 verdict computed from assertions, ADR-0004 MCP surface as plain tools,
ADR-0005 local-first with optional service mode. Nothing is Accepted yet. See the [decision log](../decisions/README.md).
The predecessor's decisions (AskOverlay ADR 0001 to 0008) stay in the `askoverlay` repository.

## Evidence we have

Only the predecessor's pointing experiment (about 85% right control, about 80% on small controls, one judge): summarised
in [predecessor evidence](../05-evaluation/predecessor-evidence.md). No measurement of the test agent exists yet.

## Exact next step

**Right now the project is waiting for the owner.** The single next step is the outside review: the owner sends
[REVIEW-BRIEF](../REVIEW-BRIEF.md) to a reviewer (as of 2026-10-12 it is being sent; not confirmed received) and pastes the
reply into a copy of the [review feedback template](../templates/review-feedback-template.md), in a fresh chat started with
the [kickoff prompt](../handoff/kickoff-prompt.md). Until the reply arrives an agent should not start the steps below: it
may fix documentation gaps, answer questions and record the owner's answers to the open questions.

After the reply arrives, in this order:

1. **Triage the feedback** (accept, reject, defer; record why), apply accepted changes to the documents on a branch, and
   open a pull request.
2. Merge the plan, tag `plan-v0.1`, then decide ADR-0001 to ADR-0005 (Accepted or Rejected). Independent cold-start
   drills were run on 2026-10-12 (narrow fail) and 2026-10-15 (pass) (see the [drill log](drills.md)); repeat it on the
   merged plan.
3. If ADR-0001 is accepted, start **R1.0** of the [roadmap](../03-features-and-roadmap.md): the seeded-bug test bed, the
   30-test suite and the **frozen pass bar**, with **no agent code before the bar is frozen**
   (see [evaluation strategy](../05-evaluation/evaluation-strategy.md)).

## Open questions

See [open questions](../07-open-questions.md). **Awaiting the owner's answers:** the product name (OQ-01; SapienZero is the
working name in use) and whether the repository stays public (OQ-12; it is public now). Also blocking: licence, which
predecessor pieces to reuse, the owner's weekly time budget, and which LLM provider(s) the first measurements use.

## Housekeeping and risks (known, not yet fixed)

- The repository is **public**, so everything committed is world-readable: never commit keys, `.env` files or private data.
  Secret scanning with push protection is on. CodeQL and dependency review are available and still to be added.
- The first GitHub Actions run passed (see above), and pull-request runs also passed (PRs 1 to 4).
- Two Dependabot pull requests are open and not yet reviewed: 5 (`actions/checkout` 4 to 7) and 6
  (`actions/setup-python` 5 to 7). Review them as ordinary CI changes; they are not urgent.
- Repository settings from the engineering handbook (section 9) were **applied on 2026-10-12** and are recorded in
  [settings-2026-10-12](../runbooks/settings-2026-10-12.md). A direct push to `main` was tested and rejected. Not yet done:
  pinning actions by commit SHA, CodeQL, dependency review, environments (not needed before deployment exists).
- Whether prompts sent through a **free-tier** Gemini key may be used by Google to improve its products is unverified
  (OQ-06); this matters before claiming that screenshots are never stored.
- Action SHA pinning is pending a tool.
- Trademark and domain checks for the name "SapienZero" are not done.

## Last session

2026-10-15: a fresh agent ran the cold-start drill from the kickoff prompt: **pass** (see the [drill log](drills.md)).
Fixed the gaps it found: "decisions in force" wording in the drill prompt and the kickoff prompt, stale PR counts in
this file; noted the two open Dependabot pull requests. Verified: documentation check (0 warnings), 31 tests, lint, CI
green on PR 4. **Not verified:** a Mermaid parse (no diagram changed); the review has still not arrived.

Earlier, 2026-10-12: created the repository by importing the plan from the AskOverlay branch `docs/plan-v0.1` (tag
`archive/sapienzero-plan-v0.1`): dropped the predecessor's decisions 0001 to 0008, renumbered the five test-agent decisions
to ADR-0001 to ADR-0005, renamed the package to `sapienzero`, rewrote CI and Dependabot for a repository without product
code, added the predecessor-evidence page, the kickoff prompt and the review feedback template. Not copied on purpose: the
overlay application code, the evaluation harness, any private data, keys and Docker files.
Then, the same day: closed and reopened OQ-01 and OQ-12 at the owner's request (both open, working answers SapienZero and
public); applied the GitHub settings ([record](../runbooks/settings-2026-10-12.md)); ran the first independent cold-start
drill (narrow FAIL, 14 gaps; see [drill log](drills.md)) and fixed the documentation gaps it found.
Verified: documentation check, 31 tests, lint (in a clean environment), CI on GitHub (green), a rejected direct push to
`main`, the drill by a fresh agent. **Not verified:** a second drill after the fixes; a full Mermaid parse of the diagrams in
this repository (manual step, done in the predecessor before the import); the review has not happened yet.
