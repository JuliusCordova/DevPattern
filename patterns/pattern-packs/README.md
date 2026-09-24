# PA-SDD Pattern Packs

Pattern Packs are reusable engineering capabilities that can be composed into a product specification.

They are **not mandatory layers**. A project should select only the packs needed to reduce ambiguity, risk, implementation effort, or operational uncertainty.

## Core agent patterns

| Pack | Use when | Avoid when |
|---|---|---|
| [AI Workflow](ai-workflow.md) | Flow is mostly deterministic | Model must choose next steps dynamically |
| [Single Agent](single-agent.md) | One agent can own the task with clear tools | Prompt/tool complexity becomes unstable |
| [Tool Calling](tool-calling.md) | Agent must read or act on external systems | A plain model response is sufficient |
| [Multi-Agent Manager](multi-agent-manager.md) | Central orchestrator needs specialists | One agent can still reliably do the job |
| [Handoff](handoff.md) | Ownership should move between specialists | Central synthesis/control is required |
| [Human-in-the-Loop](human-in-the-loop.md) | High-risk or ambiguous actions need human control | Action is low-risk and reversible |
| [Memory](memory.md) | Prior interactions/preferences materially improve future runs | Stateless behavior is sufficient |
| [Governed Agent](governed-agent.md) | Enterprise permissions, audit, security or policy matter | Temporary low-risk demo with synthetic data |

## Knowledge & data patterns

| Pack | Use when | Avoid when |
|---|---|---|
| [RAG](rag.md) | Answers require grounded private/domain knowledge | Corpus is tiny or fits safely in context |
| [GraphRAG](graphrag.md) | Questions depend on relationships/global corpus structure | Plain retrieval already performs well |
| [NL-to-SQL](nl-to-sql.md) | Users need governed conversational analytics | Direct reports/queries already solve the need |
| [Semantic Layer](semantic-layer.md) | Business meaning must be consistent across AI and analytics | Raw schema is trivial and stable |
| [Agentic Data Pipeline](agentic-data-pipeline.md) | Agents can accelerate data engineering while execution remains governed | A deterministic pipeline is already sufficient |

## Interoperability patterns

| Pack | Use when | Avoid when |
|---|---|---|
| [MCP](mcp.md) | Tools/context must be portable across agents or clients | A local in-process function is simpler |
| [A2A](a2a.md) | Independently deployed agents must collaborate across boundaries | Agents live in the same process and lifecycle |

## Runtime & execution patterns

| Pack | Use when | Avoid when |
|---|---|---|
| [Event-Driven Agent](event-driven-agent.md) | Events should trigger agentic work asynchronously | A synchronous request is enough |
| [Long-Running Agent](long-running-agent.md) | Tasks need durable progress/resume/cancel | Work completes comfortably in one request |
| [Sandboxed Code Execution](code-execution.md) | Iterative code/data work is required | Deterministic services already provide the result |

## Quality & context patterns

| Pack | Use when | Avoid when |
|---|---|---|
| [Evaluation & Observability](eval-observability.md) | Agent quality and behavior must be measurable | Never omit for MVP/Product agentic systems |
| [Context Engineering](context-engineering.md) | Context must be selected, compressed, governed and cost-controlled | Tiny one-shot prompts are sufficient |

## Composition example

```yaml
mode: MVP

packs:
  - single-agent
  - tool-calling
  - rag
  - semantic-layer
  - human-in-the-loop
  - eval-observability
  - governed-agent
```

## Progressive rule

Each pack defines what is expected at:

- **FAST DEMO** — minimum implementation to validate value.
- **MVP** — repeatable, testable behavior.
- **PRODUCT** — production-grade controls and evidence.

## Selection principle

> Start with the fewest packs possible. Add one only when it solves a concrete problem.

## Escalation examples

```text
Local function
   ↓ reuse needed
MCP

Single process specialist
   ↓ independent remote ownership
A2A

Synchronous task
   ↓ durable progress needed
Long-Running Agent

RAG
   ↓ relational/global benchmark gap
GraphRAG

Physical schema
   ↓ inconsistent business meaning
Semantic Layer
```

## Implementation profiles

Pattern Packs are vendor-neutral.

Cloud-specific decisions belong in **Implementation Profiles**.

Current profile:

- [GCP Implementation Profile](../implementation-profiles/gcp/README.md)
- [GCP Pattern Pack Mapping](../implementation-profiles/gcp/pattern-pack-mapping.md)
- [GCP Proven Practices](../implementation-profiles/gcp/proven-practices.md)

The GCP profile is based both on current Google Cloud guidance and on implementation evidence from DataGob, Business Rules Silver, and PricingPrima.

## References

See [Authoritative References](references.md).
