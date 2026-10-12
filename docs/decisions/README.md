# Decision log (ADRs)

One file per architecturally significant decision. A decision is **never edited after it is accepted** except to
change its status or add a "Related" note: to change your mind, write a new ADR that supersedes the old one, so the
history of *why* stays intact. How and when to write one: see
[documentation-and-memory-policy](../06-process/documentation-and-memory-policy.md). Start from
[the template](../templates/adr-template.md).

Statuses: **Proposed** (under review), **Accepted**, **Superseded** (replaced, see the Related line),
**Rejected**, **Deprecated**.

Numbering started again at 0001 when SapienZero was created. The earlier decisions 0001 to 0008 belong to the predecessor
product and live in the `askoverlay` repository; the relevant evidence is summarised in
[predecessor evidence](../05-evaluation/predecessor-evidence.md).

| ADR | Decision | Status | Date |
|---|---|---|---|
| [ADR-0001](0001-pivot-to-an-ai-test-agent.md) | Make the product an AI test agent | Proposed | 2026-10-12 |
| [ADR-0002](0002-repository-as-the-projects-memory.md) | The repository is the project's memory | Proposed | 2026-10-12 |
| [ADR-0003](0003-verdict-is-computed-from-assertions.md) | The verdict is computed from recorded assertions, never from the model's opinion | Proposed | 2026-10-12 |
| [ADR-0004](0004-mcp-surface-as-plain-tools.md) | The MCP surface is plain tools; the experimental Tasks feature is optional | Proposed | 2026-10-12 |
| [ADR-0005](0005-local-first-core-with-optional-service-mode.md) | A local-first core, with a designed but unbuilt service mode | Proposed | 2026-10-12 |
