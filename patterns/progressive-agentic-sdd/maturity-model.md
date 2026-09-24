# PA-SDD Maturity Model

PA-SDD increases engineering rigor progressively.

| Dimension | FAST | MVP | PRODUCT |
|---|---|---|---|
| Goal | Validate idea | Validate product | Operate safely |
| Spec | Mini Spec | Full feature spec | Governed living spec |
| Architecture | Simple feature slice | Boundaries where justified | Stronger boundaries for critical capabilities |
| Agent design | Minimal | Explicit contract where needed | Governed contract + policies |
| Evals | Smoke / basic scenarios | Golden eval set | Golden + adversarial + regression |
| Security | Basic hygiene | Relevant controls | Production controls |
| Observability | Minimal | Core telemetry | Full operational telemetry |
| Evidence | Demo evidence | Automated evidence | Promotion evidence |
| Release | Manual/demo | Controlled | Governed promotion + rollback |

## Rule

A product does not move to a higher level because time passed.

It moves because **risk, maturity, integrations, users, or operational expectations increased**.

## Anti-overengineering principle

Do not import PRODUCT complexity into FAST unless a concrete risk justifies it.
