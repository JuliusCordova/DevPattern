---
name: enterprise-agentic-architecture
description: Design, assess and industrialize enterprise agentic architectures progressively from FAST DEMO/PoC to governed MVP and PRODUCT, including Agentic TOM, Agent Contracts, PROXI decision/control, Agentic Economics, AI TRiSM, AgentOps, MCP, A2A, RAG/GraphRAG and multi-platform mappings.
---

# Enterprise Agentic Architecture Skill

Use this skill when the task is to design, review, package or evolve an enterprise agentic architecture, operating model or reusable agentic offering.

## Core thesis

**Do not build a super-agent. Coordinate governed capabilities.**

Architecture grows with **risk, maturity and executable evidence**, not with diagram complexity.

Use the DevPattern PA-SDD progression:

1. **EXPLORE — FAST DEMO / Sandbox / PoC**: prove behavior and value.
2. **GOVERN — MVP**: prove repeatability, integration and control.
3. **INDUSTRIALIZE — PRODUCT**: prove security, resilience, governance and scale.

Promotion is evidence-driven, never calendar-driven.

## Seven logical planes

1. Experience Plane
2. Agentic Orchestration & Execution Plane
3. Knowledge & Action Plane
4. AI Governance & Risk Plane
5. Security, Identity & Policy Enforcement Plane
6. AgentOps / Trust / Economics Plane
7. Agent Factory & Lifecycle Plane

Treat **PROXI** as a transversal Decision & Control Plane: it evaluates policy, risk, autonomy and runtime constraints. It must not become another business orchestrator.

## Routing model

Keep three routing decisions explicit and independently observable:

- **Capability Routing** — who should resolve the intent?
- **Knowledge Routing** — which source/strategy is needed: RAG, GraphRAG, Knowledge Graph, semantic/structured data, MCP/API or hybrid?
- **Model Routing** — which approved model class is sufficient for complexity, risk, SLA, cost and confidence?

Prefer deterministic rules first, model-assisted routing second, and abstention/escalation when confidence is insufficient.

## Agent hierarchy

Default enterprise pattern:

Experience → Enterprise Master → Capability Registry → Domain Orchestrators → Specialist Agents → Tools/Data.

The Master interprets intent, selects capabilities, coordinates domains and consolidates evidence. It must not absorb domain logic or bypass domain authorization.

Cross-domain collaboration returns to the Master for consolidation unless a justified A2A pattern explicitly requires otherwise.

## Interoperability

- **A2A**: horizontal agent↔agent / domain↔domain interoperability.
- **MCP**: vertical agent↔tool/context/data interoperability.
- **OpenTelemetry**: portable cross-runtime observability.

Do not introduce A2A or MCP merely for sophistication. Introduce them when they reduce coupling, enable independent ownership/runtime boundaries, improve governance or create reuse.

## Knowledge plane

Model knowledge as a governed set of strategies:

RAG + GraphRAG + Knowledge Graph + Semantic Layer + Structured Data + APIs/MCP + governed memory.

RAG and GraphRAG are complementary. Use GraphRAG only when relational/global reasoning gaps are demonstrated.

Apply Minimum Necessary Context. Govern allowed, required, forbidden and maximum context, cross-domain sharing, retention and memory.

## Agent Contract

Treat the Agent Contract as a **living passport** connecting architecture, governance, security, operations and lifecycle.

Minimum contract domains:

- identity, owner, domain, version and environment;
- purpose, outcomes, scope and out-of-scope;
- capabilities and input/output schemas;
- autonomy tier and risk tier;
- data classification and allowed sources;
- knowledge strategy and provenance requirements;
- allowed context and memory policy;
- allowed tools/MCP servers and scopes;
- approved model policy and model-routing rules;
- confidence, evidence and abstention thresholds;
- human approval and escalation;
- SLO, timeout, retry, concurrency and budget;
- observability/eval requirements;
- certification, lifecycle state, expiry and rollback target.

Progress contracts from **Lite → Complete → Machine-readable/Enforced** as maturity increases.

Also use Tool, Data, Knowledge, A2A Capability, MCP, Model Policy, Human Approval and SLO contracts when justified.

## Agentic TOM

The Target Operating Model must answer:

**Who decides? Who builds? Who certifies? Who operates? Who is accountable?**

Prefer a federated model:

- Strategic AI Committee: risk appetite, investment, enterprise principles and material exceptions.
- Operational AI Committee: prioritization, risk tier, gates and production readiness.
- Agentic Platform / CoE: patterns, registries, reference architecture, factory, interoperability and observability.
- Domain Product Teams: business outcome, rules, data, domain evals and functional ownership.
- AI/Agent Engineering: orchestration, instructions, tools and routing.
- Data & Knowledge Engineering: RAG, GraphRAG, semantic layer, KG, data products and freshness.
- Security/Risk/Compliance: threat model, IAM, privacy, DLP, red teaming and assurance.
- AgentOps/SRE: SLO, tracing, incidents, reliability, rollback and economics.
- Human Approvers: risk-based approvals and segregation of duties.

Central platform sets standards and controls; domains retain business ownership.

## Autonomy model

Use a progressive autonomy scale:

- A0 Inform
- A1 Recommend
- A2 Prepare; human approves before execution
- A3 Execute reversible actions under policy and logging
- A4 Execute critical actions only with reinforced approval, SoD and controls

## AI Governance and AI TRiSM

Governance decides what is allowed and who is accountable.
Security/Policy Enforcement technically enforces those decisions.
AgentOps provides evidence.

Cover portfolio/inventory, risk/autonomy, models, data/knowledge, agents, tools/MCP, A2A trust, human oversight, assurance, incidents and resilience.

Treat AI TRiSM as a transversal Trust/Risk/Security management framework, not as a single technology component.

## Agent Factory

Use the lifecycle:

Idea → Use Case → Spec → Agent Contract → Build → Eval → Security → Register → Deploy → Observe → Improve/Retire.

Use gates:

- G0 Business
- G1 Architecture
- G2 Data & Security
- G3 Evals / Trust
- G4 Production
- G5 Continuous Assurance

An agent may exist in the AI Governance Registry before it is invocable. It becomes discoverable in the Capability Registry only after required certification.

## AgentOps and Agentic Economics

Measure infrastructure, model, agent, routing, quality, security, human intervention, business outcome and economics.

Preferred economic North Star:

**Cost per successful and trusted outcome.**

Do not optimize token cost in isolation. Include retries, tool calls, model escalation, human effort, latency and business value.

## Multi-platform rule

Keep logical patterns vendor-neutral. Map them to Azure, GCP, AWS or Fabric through Component Architecture Profiles.

Prefer **one capability, one authoritative runtime**. Do not duplicate a domain across clouds without a strong resilience, regulatory or locality reason.

## Evidence-driven promotion

A production candidate should demonstrate, as applicable:

functional acceptance + golden evals + routing evals + groundedness/evidence + tool-use evals + security checks + human-approval tests + cost thresholds + SLO readiness + rollback readiness.

New production failures and edge cases should return to the golden dataset/regression suite.

## Asset catalog

When packaging reusable assets, maintain at minimum:

- Portfolio Management Agent
- Reconciliation & Quadrature Agent
- Business Rules Agent
- Legal Agent
- Project Intake Agent

For each asset capture capability, domain, maturity, Agent Contract, architecture, knowledge strategy, tools/MCP, evals/evidence, owner, risk/autonomy, platform, G0–G5 status and cost/outcome.

## Origin and attribution

This framework consolidates recurring needs observed across work and opportunities involving RIMAC, PRIMAX, KMMP, Mibanco, Pacífico Salud and La Tinka.

The concepts **PROXI Agents** and **Agentic Economics** include valuable contributions from **Henry Wong** and should be acknowledged when this framework is presented as collaborative work.

## Required output behavior

When using this skill:

1. Start from business outcome and maturity level.
2. Select the simplest architecture that protects the next stage.
3. Make assumptions and missing evidence explicit.
4. Separate logical architecture from cloud implementation.
5. Make governance, contracts, evals and operational evidence first-class.
6. Avoid vendor lock-in at the pattern layer.
7. Never add multi-agent, GraphRAG, A2A, MCP or heavy governance without a stated reason.
8. End with the evidence/gates required for the next maturity level.

## Databricks-derived execution patterns

For Master orchestration, PROXI runtime control and Agentic Economics, apply the reusable conclusions in `references/databricks-derived-patterns.md`:

- evidence-based capability selection;
- independent judge + deterministic gates;
- Monotonic Trust Guard against silent regression;
- capability health demotion/quarantine/recovery;
- durable artifact handoffs instead of hidden chat state;
- Agentic Currency using **Trusted Outcome Credit** as the normalized cost of a successful, trusted outcome;
- controlled self-improvement through eval → gate → canary → promote/revert.

These are DevPattern generalizations inspired by the Databricks Vibe Data Modeling implementation; do not attribute the DevPattern terminology itself to Databricks.

See `references/architecture-blueprint.md`, `references/agent-contract-template.md` and `references/databricks-derived-patterns.md`.
