# Cost-Aware Component Selection

DevPattern selects cloud components progressively with explicit cost awareness.

## Principle

> Use the least expensive component set that satisfies the current requirement and preserves a reasonable path to the next maturity stage.

Two rules apply together:

> Never pay for scale, resilience, isolation, or operational complexity before the requirement exists.

> Never choose a cheap component that creates an unnecessarily expensive migration trap.

## Selection flow

```text
Requirement
   ↓
Minimum architecture
   ↓
Cheapest viable component set
   ↓
Validate quality + operability + cost
   ↓
Trigger reached?
   ├─ NO → keep current mapping
   └─ YES → evolve only the affected component
```

## Cost progression

### FAST DEMO

Optimize for:
- scale-to-zero;
- consumption pricing;
- small managed tiers;
- shared capacity;
- minimal networking;
- no unnecessary HA;
- no dedicated clusters;
- synthetic/controlled data where appropriate.

### MVP

Add only when required:
- managed PaaS;
- autoscaling;
- dedicated identity;
- secrets;
- observability;
- repeatable CI/CD;
- managed persistence;
- baseline resilience.

### PRODUCT

Add only when justified:
- HA;
- multi-zone;
- private networking;
- dedicated capacity;
- replicas;
- DR;
- stronger isolation;
- reserved/committed capacity;
- advanced observability;
- enterprise support controls.

## Escalation triggers

A component may evolve when one or more of these are observed:

- sustained traffic;
- cold starts affect the SLO;
- concurrency limits are approached;
- background/asynchronous work appears;
- RPO/RTO requires stronger persistence;
- workload requires isolation;
- data sensitivity increases;
- operational support requires stronger controls;
- monthly cost becomes less efficient than a higher fixed tier;
- latency/cost benchmark proves a different component is better.

## Component-level escalation

Do not escalate the whole architecture when only one component needs to change.

Example:

```text
Cloud Run scale-to-zero
   ↓ sustained workload
Cloud Run with minimum instances
   ↓ runtime limitation proven
Evaluate alternative runtime
```

not:

```text
Cloud Run
   ↓
Kubernetes by default
```

## LLM cost strategy

Use model routing where it produces measurable benefit.

```text
simple task
   ↓
small/cheap model

normal task
   ↓
balanced model

complex reasoning
   ↓
stronger model
```

Measure:

- cost per successful outcome;
- quality;
- latency;
- retry rate;
- tool calls.

Do not optimize model cost in isolation from outcome quality.

## RAG progression

### FAST DEMO
- simple chunking;
- small vector index;
- basic retrieval;
- citations where feasible.

### MVP
- metadata;
- hybrid retrieval where useful;
- eval benchmark;
- ingestion lifecycle.

### PRODUCT
Only if measured improvement justifies cost:
- reranking;
- permission-aware retrieval;
- GraphRAG;
- advanced indexing;
- distributed retrieval architecture.

## Database progression

```text
FAST DEMO
small/local/serverless persistence

MVP
managed database + backups + monitoring

PRODUCT
HA / replicas / private access / DR
only when RPO, RTO, load, or business criticality requires it
```

## Key rule

> Scale architecture with evidence, not anticipation.
