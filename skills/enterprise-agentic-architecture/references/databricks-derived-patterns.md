# Patterns Extracted from Databricks Vibe Data Modeling

Source studied: `databricks-industry-solutions/lakehouse-industry-data-models`, especially `model-agent` and `model-genie-skills`.

> These are **DevPattern interpretations**, not claims that Databricks defines an Enterprise Master Agent, PROXI, or Agentic Currency. The source provides implementation patterns that can be generalized into those concepts.

## Source-grounded observations

The Databricks implementation demonstrates several reusable engineering ideas:

1. **One authoritative intent outranks heuristics.** Explicit user/business instructions take priority over heuristics, scores and LLM opinions.
2. **Generation is not acceptance.** A generated artifact is validated through deterministic structural gates and architect/judge review before it advances.
3. **A bad refinement must not become the new baseline.** The modeling pipeline includes a monotonic guard that can revert a pass that makes the model worse.
4. **Use different models for different jobs.** The implementation uses a multi-model ensemble: stronger reasoning/review models for difficult decisions and smaller/worker models for high-volume or simpler work.
5. **The runtime can self-heal model selection.** Failing models can be demoted and restored when healthy.
6. **Version and compare every material change.** Natural-language refinements create versioned models that can be compared before deployment.
7. **Handoffs should be durable artifacts, not hidden chat state.** The Genie skills pass assessment → build → validate → document through explicit documents.
8. **Human gates remain at decision points.** The integration workflow is deliberately phase-gated rather than an unconstrained roaming agent.
9. **Scratchpad → validate → confirm → persist.** Work is provisional until validation and confirmation succeed.
10. **Quality should be computed from evidence.** Structural quality is computed from the actual model rather than relying on an LLM self-assessment.
11. **A single source of truth plus clean graph boundaries reduces ambiguity.** The source enforces ownership and graph integrity rather than allowing duplicated concepts and arbitrary cycles.
12. **Every run can improve the system.** The skill loop emits improvement recommendations and supports synchronization after changes.

## Pattern A — Master Agent as governed coordinator

### Intent

The Enterprise Master should behave less like an all-knowing super-agent and more like a **governed coordinator of competing/available capabilities**.

### Pattern

```text
Business Intent
      |
      v
Enterprise Master
      |
      +--> Capability candidates
      |       |
      |       +--> domain agents
      |       +--> specialist agents
      |       +--> deterministic services
      |
      +--> PROXI eligibility / constraints
      |
      +--> route + execute
      |
      +--> independent validation / judge
      |
      +--> evidence + outcome
      |
      +--> compare with current baseline
      |
      +--> accept | retry differently | escalate | revert
```

### Rules

- Business intent and explicit policy constraints outrank model preference.
- The Master does not certify its own result when an independent evaluator is justified.
- Candidate capabilities are selected by fitness, policy, health, quality and economics.
- Failed attempts should change strategy rather than blindly repeat.
- Material outputs are versioned and comparable.
- A new result only replaces a trusted baseline when promotion criteria are met.
- Cross-domain state is exchanged through explicit contracts/evidence, not opaque conversational memory.

### Why it matters

This turns the Master from a router into a **portfolio coordinator with evidence-based promotion**, while keeping domain knowledge and execution decentralized.

## Pattern B — Agentic Currency

### Intent

Create a common unit for comparing heterogeneous agent/model/tool execution paths without reducing economics to token price.

### Definition

**Agentic Currency** is the normalized economic representation of a candidate execution path.

It should be derived from observed evidence, not assigned as an arbitrary token.

Recommended unit:

> **Trusted Outcome Credit (TOC)** — economic cost required to obtain one successful, policy-compliant, evidence-backed outcome at the required SLO.

### Candidate cost envelope

```text
TOC cost =
  model inference
+ tool/API execution
+ data/knowledge retrieval
+ orchestration
+ retries/rework
+ validation/evals
+ human intervention
+ infrastructure
+ risk/control overhead
```

The denominator is not "requests." It is **successful and trusted outcomes**.

### Economic score for routing

For candidate route `r`:

```text
Expected Trusted Outcome Cost(r)
  = Expected Execution Cost(r)
    / P(success AND trusted | r)
```

PROXI/Master may use this together with hard policy constraints and SLOs. The cheapest route is not automatically preferred; an inexpensive route with poor success probability can have worse expected economics.

### Databricks-derived insight

The source's role-specialized model ensemble suggests a general principle: **do not spend frontier-model economics on every subtask**. Allocate expensive reasoning to the stages where it changes outcome quality; use cheaper workers for bounded/high-volume work, and promote/escalate only when evidence warrants it.

### Ledger

AgentOps should emit a ledger entry per meaningful execution:

```yaml
agentic_economics:
  trace_id: ""
  capability_id: ""
  route_id: ""
  model_policy: ""
  tool_calls: 0
  retries: 0
  human_minutes: 0
  latency_ms: 0
  direct_cost: 0
  control_cost: 0
  outcome_success: false
  trusted: false
  trusted_outcome_credit_cost: null
```

Aggregate by capability, agent, domain, model policy, route and business outcome.

## Pattern C — PROXI Agents / Decision & Control Plane

### Intent

PROXI should make runtime permission and resource-allocation decisions **before and after** execution. It is not the domain orchestrator.

### Pre-execution decision

Evaluate:

- identity and entitlement;
- capability certification;
- autonomy/risk tier;
- data/context classification;
- allowed model policy;
- allowed tools/MCP/A2A peers;
- health;
- SLO;
- budget / Agentic Currency envelope;
- required human approval.

Output:

`ALLOW | DENY | CONSTRAIN | ROUTE | REQUIRE_APPROVAL | ESCALATE`

### Post-execution decision

Evaluate:

- deterministic invariants;
- golden/adversarial evals;
- evidence/groundedness;
- security/policy events;
- actual cost vs budget;
- SLO;
- comparison with trusted baseline.

Output:

`ACCEPT | RETRY_DIFFERENTLY | ESCALATE | QUARANTINE | REVERT`

### Monotonic Trust Guard

Generalize the Databricks monotonic guard:

> A new agent/model/prompt/tool/route version must not silently replace the trusted baseline when measured trust deteriorates beyond the approved tolerance.

```text
Candidate
   |
   v
Evaluation vs Golden + Current Production
   |
   +-- better / within tolerance --> eligible for promotion
   |
   +-- worse --> reject / revert / investigate
```

"Better" must be multidimensional: quality, groundedness, safety, reliability, latency and Trusted Outcome Cost, with policy-defined weights and hard floors.

### Self-healing capability roster

Generalize model demotion/recovery into a capability-health pattern:

- healthy capability → routable;
- degraded capability → lower routing priority;
- failed/circuit-open capability → temporarily unroutable;
- recovered capability → canary + re-evaluation before full restoration.

PROXI owns the decision state; execution remains with gateways, identities, policy engines and domain runtimes.

## Pattern D — Artifact Handoff Contract

For multi-agent or multi-stage work, prefer explicit, versioned handoff artifacts over hidden chat state.

```text
Discover/Assess
   -> assessment artifact
Plan/Build
   -> build manifest
Validate
   -> validation evidence
Promote
   -> release evidence
Operate
   -> telemetry + improvement recommendations
```

Each artifact should include producer, consumer, schema/version, evidence, assumptions, unresolved gaps and approval state.

This pattern complements A2A: A2A defines communication; the handoff artifact defines the durable business/engineering state being transferred.

## Pattern E — Judge and deterministic gates

Do not use "LLM-as-judge" as the only trust mechanism.

Use:

1. deterministic invariants for things that can be objectively checked;
2. domain/business golden cases;
3. evaluator/judge models for semantic dimensions;
4. human review for high-risk ambiguity;
5. comparison against the current trusted baseline.

The evaluator should not be the same execution path whenever independence materially reduces correlated failure.

## Pattern F — Controlled self-improvement

Continuous improvement should be a governed loop:

```text
Production evidence
  -> failure / edge case / economic anomaly
  -> candidate improvement
  -> golden/adversarial dataset
  -> candidate version
  -> evaluation
  -> PROXI promotion decision
  -> canary
  -> production or revert
```

Agents may propose improvements; they must not autonomously rewrite the trusted baseline without the required gates.

## DevPattern implications

Add these principles to Enterprise Agentic Architecture:

- Master = portfolio coordinator, not super-agent.
- PROXI = runtime decision/control + pre/post execution assurance.
- Agentic Currency = normalized economics for routing and portfolio decisions.
- Trusted Outcome Credit = recommended economic unit.
- Monotonic Trust Guard = no silent regression.
- Capability Health Roster = demote, quarantine, canary and restore.
- Durable Artifact Handoffs = documents/contracts over hidden chat state.
- Independent Evaluation = deterministic + semantic + human according to risk.
- Controlled Self-Improvement = production evidence feeds governed regression/promotion.

## Source boundary

Databricks' repository is a data-modeling and data-integration implementation. It does **not** present these DevPattern terms as an enterprise agentic standard. Master Agent, PROXI, Agentic Currency, Trusted Outcome Credit and the enterprise generalizations above are derived architectural patterns inspired by the demonstrated mechanisms.
