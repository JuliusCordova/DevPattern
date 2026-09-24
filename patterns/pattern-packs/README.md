# PA-SDD Pattern Packs

Pattern Packs are reusable engineering capabilities that can be composed into a product specification.

They are **not mandatory layers**. A project should select only the packs needed to reduce ambiguity, risk, or implementation effort.

## Core catalog

| Pack | Use when | Avoid when |
|---|---|---|
| AI Workflow | Flow is mostly deterministic | Model must choose next steps dynamically |
| Single Agent | One agent can own the task with clear tools | Prompt/tool complexity becomes unstable |
| Tool Calling | Agent must read or act on external systems | A plain model response is sufficient |
| RAG | Answers require grounded private/domain knowledge | Corpus is tiny or fits safely in context |
| GraphRAG | Questions depend on relationships/global corpus structure | Plain retrieval already performs well |
| Multi-Agent Manager | Central orchestrator needs specialists | One agent can still reliably do the job |
| Handoff | Ownership should move between specialists | Central synthesis/control is required |
| Human-in-the-Loop | High-risk or ambiguous actions need human control | Action is low-risk and reversible |
| Memory | Prior interactions/preferences materially improve future runs | Stateless behavior is sufficient |
| Governed Agent | Enterprise permissions, audit, security or policy matter | Temporary low-risk demo with synthetic data |

## Composition example

```yaml
mode: MVP

packs:
  - single-agent
  - tool-calling
  - rag
  - human-in-the-loop
  - governed-agent
```

## Progressive rule

Each pack defines what is expected at:

- **FAST** — minimum implementation to validate value.
- **MVP** — repeatable, testable behavior.
- **PRODUCT** — production-grade controls and evidence.

## Selection principle

> Start with the fewest packs possible. Add one only when it solves a concrete problem.
