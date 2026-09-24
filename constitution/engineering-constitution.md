# PA-SDD Engineering Constitution

This constitution defines the non-negotiable engineering principles for projects adopting Progressive Agentic Spec-Driven Development.

## 1. Spec before implementation
Every feature begins with a minimum sufficient specification describing intent, expected outcome, boundaries, and acceptance criteria.

## 2. Minimum sufficient ceremony
Artifacts are created only when they reduce ambiguity, risk, rework, or operational uncertainty.

## 3. Patterns before reinvention
Projects should compose reusable patterns instead of redefining architecture, security, evaluation, or operational practices.

## 4. Simplicity before autonomy
Prefer deterministic software or workflows when they solve the problem. Introduce agents only when dynamic reasoning or tool selection adds material value.

## 5. Single agent before multi-agent
Multi-agent architectures must be justified by context isolation, specialization, security boundaries, scale, or orchestration needs.

## 6. Contracts before integration
Agents, tools, APIs, data exchanges, and external dependencies should expose explicit contracts.

## 7. Evals before trust
Agentic behavior is considered reliable only when evaluated against representative scenarios and measurable expectations.

## 8. Evidence before promotion
Production promotion requires executable evidence such as tests, evals, security checks, smoke tests, and operational readiness.

## 9. Security and permissions by design
Least privilege, permission-aware behavior, secrets management, data protection, and auditable actions are built into the design.

## 10. Human control for high-risk actions
Irreversible, sensitive, or high-impact actions require explicit approval or an equivalent risk control.

## 11. Observable by default
Production-ready systems must expose enough telemetry to understand quality, latency, failures, tool use, cost, and business outcomes.

## 12. Cost is an architecture metric
Agentic systems must measure cost per successful outcome, not tokens alone.

## 13. Reversible delivery
Deployments should support rollback, versioning, and controlled promotion.

## 14. Every meaningful failure becomes an eval
Production incidents and important defects must enrich the regression and evaluation suite.

## 15. Specs evolve with the product
Specifications are living engineering assets and must remain aligned with product behavior.
