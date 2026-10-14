# Cold-start drill log

Status: living document. Procedure: [documentation and memory policy](../06-process/documentation-and-memory-policy.md)
section 7. Record every drill here, including failures; a drill that found gaps is a success.

| Date | Commit | Agent and setup | Result (six answers, small task) | Gaps found and fixed |
|---|---|---|---|---|
| 2026-10-12 | AskOverlay branch `docs/plan-v0.1` before the import | **Author's own cold read, not independent, does not count** | Answers a to f were derivable; the exact next step was clear | Found and fixed before the import: an obsolete step name in STATUS, and that the work had not been pushed to GitHub |
| 2026-10-12 | `ae7a529` | **Independent**: a fresh subagent with no context, fresh clone, read-only, told only "Read AGENTS.md and follow the cold-start steps" | **Narrow FAIL.** Answered a to f correctly from the repository alone and verified six factual claims (76 requirements, 31 tests, 23 documents in the map, 5 ADRs, job names, history). Failed the bar "name the next step without asking" | 14 gaps, all verified against the files. Fixed in the same change: stale CI/CD status (workflows described as never run, protection as pending); policy said a stale date or missing template exemption "fails CI" but the checker warns after 14 days and checks reachability; required-checks list named jobs that do not exist; no command for Mermaid validation (now stated as manual); no venv commands (added for three shells); STATUS "Decisions in force" listed only Proposed decisions (renamed); next step was four items with an unknown owner action (now one waiting step); "10 minutes" was an agent figure (human 30 to 40 min). Left as is, with reasons below |
| 2026-10-15 | `6241828` | **Real fresh-agent drill** (Claude Code, new chat, no prior chat or memory), started with the [kickoff prompt](../handoff/kickoff-prompt.md) pasted by the owner. Not a fresh clone: the owner's own checkout, clean, on `main` | **PASS.** Answered a to f from the repository alone and named the next step (wait for the reviewer) without asking. Re-verified: 76 requirements, 23 documents in the map, 5 ADRs all Proposed, docs check passed (0 warnings), 31 tests passed, lint passed, CI green on PR 4. Small task: recorded this drill and fixed the gaps below | 3 gaps. Fixed: the drill prompt in the policy (section 7) and the kickoff prompt still asked for "three decisions in force" although none is in force (question c here was already corrected); STATUS said CI was green on PRs "1 to 3" and elsewhere "1 and 2" (now 1 to 4, PR 4 checked). Recorded in STATUS: two open Dependabot pull requests (5 and 6, action version bumps) that no document mentioned |
| (pending) | | **Second independent drill on the merged plan, after the reviewer's feedback is applied** | | |

Gaps knowingly left: the kickoff prompt and settings record hold machine-specific paths (`D:\Projects\...`) because they
describe the owner's actual setup; the predecessor's evidence is summarised here but verifiable only in the other repository;
`.env.example`, `docs/reviews/` and `src/` paths named in CODEOWNERS do not exist yet (they are created when needed). The drill
subagent could not record its own result (it was read-only), so the owner's agent records it here: the kickoff prompt tells a
fresh chat to do the same.

## Questions asked (so results are comparable)

a. What is this project in three sentences? b. What is the current phase and the exact next step? c. Name three decisions (say whether each is Accepted or Proposed)
and why. d. How do I run the tests and the docs check? e. What is not in the repository, and how is it recovered? f. Which release
gate are we working toward and what does it require?

Small task variants (rotate): add a requirement; record a decision as an ADR and update the index; answer "what changed in
ADR-0001's status and why?"; add a lesson; update STATUS after a pretend session; list everything that changes if the product is renamed (read-only).
