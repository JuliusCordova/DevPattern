# Agentic economics, PROXI and MPP

Status: proposed architecture | Updated: 2026-10-08

## Decision
MPP belongs conceptually to agentic economics, specifically payment interoperability.
PROXI applies governance in runtime; MPP is one optional adapter in its execution gateway.
The Master coordinates the business objective. PROXI must not become a second business orchestrator.

| Plane / component | Responsibility |
|---|---|
| Governance | Ownership, risk, autonomy, spend policies, approval and revocation |
| Agentic economics | Budgets, commitments, pricing, payments, reconciliation, cost/value |
| PROXI Control Plane | Catalog, policy versions and delegated resource limits |
| PROXI Execution Gateway | Enforce authority, reserve budget and invoke approved adapters |
| MPP | Payment challenge/credential exchange with compatible services |
| AgentOps | Correlate execution, cost, quality and outcome |

PROXI's proposed layers are Edge & Identity, Understanding, Decision Engine,
Execution Gateway and Response Assurance, with Governance, AgentOps & Trust and Lifecycle
as cross-cutting planes. This document maps that design to economics; it does not claim PROXI is implemented.

## Integration points
- Decision Engine compares approved capabilities by quality, price, latency and risk.
- Governance Plane sets transaction/task/period limits, provider allowlists and autonomy.
- Execution Gateway authorizes using deterministic code and a transactional ledger.
- Payment adapter protects credentials and executes MPP according to its method.
- Response Assurance checks delivery and quality independently of payment status.
- AgentOps measures cost per successful outcome and failed-spend rate.

Internal tools need cost controls even without machine payments.
External services need MPP only when they expose a compatible payment interface.
Buying data never bypasses classification, licensing, purpose or access controls.

## Contract and evidence
See [Governed Agent Payments](governed-agent-payments.md) for invariants, logical contracts,
maturity gates and acceptance scenarios.
The [AI governance hub](https://github.com/JuliusCordova/portafoliodatagob/tree/main/docs/ai-governance)
owns the evolving governance narrative; DevPattern owns the reusable engineering pattern.
