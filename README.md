# SapienZero

An **AI test agent**. Describe a test in plain English; SapienZero runs it in an isolated, headless browser in the
background and returns **passed, failed, inconclusive, blocked or error** with evidence (screenshots, trace, step log). The
verdict is computed from assertions that were actually executed, never from the model's opinion. It works on its own (command
line, CI) or supervised by a coding agent over MCP.

> **Status: planning (R0).** There is no product code yet. The plan is a draft under review. Start with
> [`docs/00-START-HERE.md`](docs/00-START-HERE.md); the current state and exact next step are in
> [`docs/status/STATUS.md`](docs/status/STATUS.md). Working on this repository with an AI agent? Read
> [`AGENTS.md`](AGENTS.md) first.

![System overview](docs/diagrams/overview.svg)

## Where to read

| I want to... | Read |
|---|---|
| Understand the idea in one page | [Review brief](docs/REVIEW-BRIEF.md) |
| See the design | [High-level design](docs/04-architecture/hld.md), [low-level design](docs/04-architecture/lld.md) |
| See what gets built and when | [Features and roadmap](docs/03-features-and-roadmap.md) |
| Know how we work | [Engineering handbook](docs/06-process/engineering-handbook.md) |
| Start a fresh AI chat on this project | [Kickoff prompt](docs/handoff/kickoff-prompt.md) |

## Origin

SapienZero grew out of an earlier project, [AskOverlay](https://github.com/brindeshwar/askoverlay) (a desktop overlay that points
at controls on your screen). That project continues separately; what it measured is summarised in
[predecessor evidence](docs/05-evaluation/predecessor-evidence.md).

## Checks

```
python -m pip install -r requirements-dev.txt
python tools/check_docs.py
python -m pytest -q tools
python -m ruff check . --config ruff.toml
```

Licence: not chosen yet (open question OQ-02).
