# Governed Agentic Platform — Reference Alignment v4

Status: proposed reusable architecture / documentation baseline. Updated: 2026-10-08.
Source: user-supplied "Kyndryl_Arquitectura_Agentica_Referencia_v4.pdf", October 2026, 64 pages.
This is an engineering synthesis, not a publication of the deck, a corporate policy approval or evidence of runtime implementation. Market statistics and changing vendor claims are not adopted as verified requirements.

## Architectural decision

PA-SDD supplies the progressive delivery method. This composition supplies the enterprise coordination, authority and evidence around it.
Start with a feature slice; add shared platform capabilities only when risk, independent ownership or operational scale justify them.
The Master owns business coordination. PROXI is the logical decision and enforcement plane; it is not a second business orchestrator or necessarily a standalone service.
Gateways, identity services and deterministic policy code enforce its decisions.

## Seven logical planes

| Plane | Responsibility | Existing DevPattern reuse | Additional contract/evidence |
|---|---|---|---|
| Experience | Authenticated channels, requests and feedback | UI packs, HITL | Requester identity, approval status and sources |
| Agentic execution | Master, domain orchestration, specialists | Multi-agent manager, handoff, A2A | Capability registry, bounded delegation and hops |
| Knowledge and action | Grounded knowledge and authorized tools | RAG, GraphRAG, semantic layer, NL-to-SQL, MCP | Source permissions, freshness, tool scopes |
| AI governance | Ownership, contracts, autonomy and lifecycle authority | Governed agent | Versioned Agent Contract and decision rights |
| Security and policies | Enforcement at each trust boundary | Governed agent, HITL, implementation profiles | Audience/scopes, egress rules, revocation |
| AgentOps and trust | Quality, execution, cost and outcome | Eval-observability, governed payments | Decision record and accepted outcome |
| Factory and lifecycle | Promotion, regression, rollback and retirement | PA-SDD maturity/evidence | Gate packet tied to exact artifact versions |

These are responsibilities, not seven mandatory deployments.
Data governance supplies ownership, classification, quality, lineage, purpose and access constraints to knowledge, contracts and enforcement. AI readiness evaluates fitness for the use case; AI governance controls behavior and authority.

## Keep three axes separate

| Axis | Meaning | Values |
|---|---|---|
| Organizational maturity | Repeatability and operating capability | N0 exploration; N1 repeatable experimentation; N2 production case by case; N3 industrialized; N4 managed scale |
| Agent autonomy | Authority of a particular action | A0 inform; A1 recommend; A2 prepare; A3 reversible execution; A4 critical execution |
| Delivery mode | Engineering evidence for a workload | FAST DEMO, MVP, PRODUCT |

No automatic conversion: an N4 organization can operate an A0 agent; an MVP with sensitive read-only data may require a controlled route.
FAST DEMO is not permission to expose sensitive data or bypass authorization.

## PROXI: seven decision responsibilities

1. Resolve requester, agent identity and current contract.
2. Evaluate classification, purpose, autonomy, policy and budget.
3. Select a registered capability with sufficient confidence.
4. Select knowledge strategy by question and evaluation evidence.
5. Select an approved model class within latency, quality and resource limits.
6. Authorize tool scope and bind any human approval to the concrete action.
7. Check evidence and response schema; abstain or escalate when insufficient.

Router recommendations are inputs, not authority. LLM confidence alone is not a quality or security guarantee.
A classifier may help choose a route; deterministic enforcement must revalidate before every protected action.

Proposed decision record: decision_id, trace_id, run_id, agent_id, requester_ref, contract_version, policy_version, capability_id, model_class, knowledge_route, tool_scope, autonomy, reason_code, approval_ref, budget_ref and timestamp.
Keep credentials, raw prompts and sensitive responses outside the default record.

## Brownfield integration P1–P4

| Pattern | Fit | Integration condition |
|---|---|---|
| P1 domain agent | Independent owner, rules and runtime | Registered capability; A2A facade only when an actual remote boundary exists |
| P2 specialist | Bounded task inside a domain | Domain orchestrator invokes it; local calls remain valid |
| P3 tool | Deterministic lookup or action | Authorized local/API tool; MCP when portability adds value |
| P4 consolidate/retire | Duplicate, orphaned or unmeasured capability | Owner-approved disposition and historical evidence retained |

An Agent Card describes discovery capabilities; it does not replace authorization or the governing contract.
Do not add A2A for in-process specialists, GraphRAG without a demonstrated retrieval gap, or one MCP server per API by default.

## Agent Contract extension — proposed logical shape

- Identity: stable ID, owner, accountable, purpose, domain and lifecycle.
- Data: approved sources, classification, access, retention and provenance.
- Actions: tools/scopes, allowed side effects, autonomy and compensations.
- Models: approved classes/providers, data restrictions and fallback.
- Economics: task/period budget, parent delegation, currency and limit authority.
- Assurance: golden/adversarial evals, acceptance rule and abstention.
- Operations: SLO, telemetry, incident owner, kill switch and rollback.
- Versioning: contract_version, policy_version, valid_from, expiry and recertification.

Lite and full describe evidence depth; even Lite requires an owner, explicit bounds and acceptance evidence.
For payments compose [Governed Agent Payments](governed-agent-payments.md). A budget is not a wallet; payment is not accepted delivery.

## Promotion gates — operational proposal

The deck places G0–G5 across intake, design, evaluation, production and operation. The following exit criteria make that visual actionable; they are a proposed elaboration.

| Gate | Required evidence | Decision |
|---|---|---|
| G0 intake | Owner, need, scope, business KPI and baseline | Admit/reformulate |
| G1 value/risk | Tier, autonomy, sources, P1–P4 disposition and benefit hypothesis | Select route |
| G2 design/security | Contract, architecture decisions, least privilege and trust boundaries | Allow bounded sandbox |
| G3 evaluation/MVP | Golden/adversarial results as applicable, costs, failure and abstention evidence | Allow controlled pilot |
| G4 production | Functional acceptance, evals, security, observability, budget and tested rollback | Promote exact version |
| G5 operation | SLO, realized value, incidents, drift and recertification evidence | Continue/change/retire |

Fast track eligibility requires low risk, approved data, approved pattern, bounded actions and complete evidence; A0–A1 alone is insufficient.
Decision rights must have exactly one accountable per decision. COE can exercise delegated low-risk approval; controlled production goes to the operational authority; material exceptions go to strategic/risk authority.
Reconcile client-specific RACI and committee mandates before adopting these defaults.

## Economics and MPP placement

Internal consumption: meter raw provider/model tokens, normalize monetary costs, attribute with evidence, showback first.
MPP is an optional external-payment adapter under governed agent economics, not a required eighth plane.
Preserve independent states for estimated, reserved, paid, billed, delivered and accepted; reconcile rather than add them.
See [Economics / PROXI / MPP](agentic-economics-proxi-mpp.md).

Operational North Star = total cost / accepted successful and policy-compliant outcomes.
Include model, tools, infrastructure and human review using an explicit cost basis/window; if denominator is zero show unavailable and total spend, not zero unit cost.
Factory North Star = time from prioritized case to governed production. Keep intake waiting time as a separate metric.

## Progressive adoption and acceptance

FAST DEMO: one domain, synthetic data, Lite contract, fixed approved model, simulated decisions and baseline evals.
MVP: registry, versioned contract, policy checks, golden/adversarial evidence, correlated runs and bounded pilot.
PRODUCT: enforcement per trust boundary, controlled rollout, resilience, recertification and trustworthy cost/outcome evidence.
PROXI rollout: measure → shadow → controlled enforcement → scale. Shadow never substitutes for existing security controls.

Acceptance scenarios:
- Missing/expired contract cannot authorize a protected action.
- Prompt instructions cannot elevate autonomy, tool scope or budget.
- Sensitive A0 requests do not automatically qualify for fast track.
- Low routing confidence triggers evaluated fallback or abstention.
- Changed action/amount/beneficiary invalidates the old approval.
- Telemetry failure may be best-effort; authorization failure must block the protected action.
- Kill switch blocks new work; pending external commitments still require reconciliation.
- Failed-but-paid results remain in total spend and outside accepted outcomes.

## Ownership and next consumer

DevPattern owns reusable patterns and acceptance invariants.
[ATLAS DataGob alignment](https://github.com/JuliusCordova/portafoliodatagob/blob/main/docs/ai-governance/reference-v4-alignment.md) owns product mapping, decision workflows and implementation backlog.
Vendor mappings stay in component profiles and require separate current official-source verification.
