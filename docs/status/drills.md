# Cold-start drill log

Status: living document. Procedure: [documentation and memory policy](../06-process/documentation-and-memory-policy.md)
section 7. Record every drill here, including failures; a drill that found gaps is a success.

| Date | Commit | Agent and setup | Result (six answers, small task) | Gaps found and fixed |
|---|---|---|---|---|
| 2026-10-12 | AskOverlay branch `docs/plan-v0.1` before the import | **Author's own cold read, not independent, does not count** | Answers a to f were derivable; the exact next step was clear | Found and fixed before the import: an obsolete step name in STATUS, and that the work had not been pushed to GitHub |
| (pending) | | **Independent fresh agent in this repository: required for the R0 exit gate** | | |

## Questions asked (so results are comparable)

a. What is this project in three sentences? b. What is the current phase and the exact next step? c. Name three decisions in force
and why. d. How do I run the tests and the docs check? e. What is not in the repository, and how is it recovered? f. Which release
gate are we working toward and what does it require?

Small task variants (rotate): add a requirement; record a decision as an ADR and update the index; answer "what changed in
ADR-0001's status and why?"; add a lesson; update STATUS after a pretend session.
