# Workload Selector

The Workload Selector maps a software idea to the smallest useful cloud component set.

## Supported workload families

- web-app
- agentic-app
- rag-app
- event-driven
- data-platform

Microsoft Fabric uses data-centric workload names because Fabric is not the general-purpose application runtime for every software product.

## Selection flow

```text
Software idea
   ↓
What kind of workload is it?
   ↓
web / agentic / rag / event / data
   ↓
What maturity?
   ↓
FAST DEMO / MVP / PRODUCT
   ↓
What platform?
   ↓
Azure / GCP / AWS / Fabric
   ↓
What cost envelope applies?
   ↓
Select minimum component mapping
   ↓
Validate escalation triggers
```

## Core rule

> Do not select every available managed service. Select the minimum set that satisfies the current stage and cost envelope.

## Escalation triggers

Move to a richer mapping only when there is evidence of:

- more users/load;
- higher availability requirements;
- stronger security/isolation;
- more integrations;
- long-running or asynchronous execution;
- data sensitivity;
- enterprise governance;
- operational support requirements;
- measurable cost/performance constraints.

## Output expected from the selector

```yaml
workload: agentic-app
mode: MVP
platform: gcp

architecture:
  style: hexagonal-slice

pattern_packs:
  - single-agent
  - tool-calling
  - eval-observability

components:
  runtime: cloud-run
  agent_framework: adk
  model_platform: vertex-ai
  data: bigquery
  secrets: secret-manager
  observability: cloud-logging-monitoring
```


## Cost-aware selection

The selector must consider expected usage, traffic pattern, availability window, data volume, growth uncertainty, target monthly cost, hard monthly cost limit, scale-to-zero suitability, consumption pricing, and migration path.

When the selected architecture is likely to exceed the cost envelope, return three alternatives:

- **LEAN** — lower-cost viable architecture.
- **BALANCED** — recommended architecture for current maturity.
- **SCALE** — higher resilience/scale architecture.

Each option should explain what the additional cost buys.

See [Cost-Aware Component Selection](cost-aware-selection.md) and [Cost Envelope](cost-envelope.md).

## Key principle

> Scale architecture with evidence, not anticipation.
