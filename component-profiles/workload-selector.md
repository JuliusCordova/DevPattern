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
Select minimum component mapping
```

## Core rule

> Do not select every available managed service. Select the minimum set that satisfies the current stage.

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
