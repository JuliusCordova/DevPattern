# PA-SDD Pattern Packs

Pattern Packs are reusable engineering capabilities that can be composed into a product specification.

They are **not mandatory layers**. A project should select only the packs needed to reduce ambiguity, risk, or implementation effort.

## Core catalog

| Pack | Use when | Avoid when |
|---|---|---|
| [AI Workflow](ai-workflow.md) | Flow is mostly deterministic | Model must choose next steps dynamically |
| [Single Agent](single-agent.md) | One agent can own the task with clear tools | Prompt/tool complexity becomes unstable |
| [Tool Calling](tool-calling.md) | Agent must read or act on external systems | A plain model response is sufficient |
| [RAG](rag.md) | Answers require grounded private/domain knowledge | Corpus is tiny or fits safely in context |
| [GraphRAG](graphrag.md) | Questions depend on relationships/global corpus structure | Plain retrieval already performs well |
| [Multi-Agent Manager](multi-agent-manager.md) | Central orchestrator needs specialists | One agent can still reliably do the job |
| [Handoff](handoff.md) | Ownership should move between specialists | Central synthesis/control is required |
| [Human-in-the-Loop](human-in-the-loop.md) | High-risk or ambiguous actions need human control | Action is low-risk and reversible |
| [Memory](memory.md) | Prior interactions/preferences materially improve future runs | Stateless behavior is sufficient |
| [Governed Agent](governed-agent.md) | Enterprise permissions, audit, security or policy matter | Temporary low-risk demo with synthetic data |

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

## Implementation profiles

Pattern Packs are vendor-neutral.

Cloud-specific decisions belong in **Implementation Profiles**.

Current profile:

- [GCP Implementation Profile](../implementation-profiles/gcp/README.md)
- [GCP Pattern Pack Mapping](../implementation-profiles/gcp/pattern-pack-mapping.md)
- [GCP Proven Practices](../implementation-profiles/gcp/proven-practices.md)

The GCP profile is based both on current Google Cloud guidance and on implementation evidence from DataGob, Business Rules Silver, and PricingPrima.

## Progressive rule

Each pack defines what is expected at:

- **FAST** — minimum implementation to validate value.
- **MVP** — repeatable, testable behavior.
- **PRODUCT** — production-grade controls and evidence.

## Selection principle

> Start with the fewest packs possible. Add one only when it solves a concrete problem.

## References

See [Authoritative References](references.md).
