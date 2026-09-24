# Pack — Tool Calling

## Intent

Expose external capabilities to an agent through explicit, testable tool contracts.

## Tool classes

- **Data tools** — retrieve information.
- **Action tools** — change external state.
- **Orchestration tools** — invoke another agent or capability.

## Contract

```yaml
tool:
  name:
  description:
  input_schema:
  output_schema:
  side_effect: false
  reversible: true
  risk: low
  timeout:
  retries:
  permissions:
  audit:
```

## Design rules

- names and descriptions must be unambiguous;
- use structured inputs/outputs;
- keep business logic outside tool descriptions;
- mark write/irreversible actions explicitly;
- isolate vendor SDKs behind adapters;
- log tool invocation and outcome.

## FAST
- direct function tools;
- schema validation;
- smoke tests.

## MVP
- explicit contracts;
- timeouts/retries;
- tool-selection evals;
- error handling.

## PRODUCT
- risk classification;
- approvals for sensitive tools;
- least privilege;
- audit trail;
- idempotency where relevant.

## Key rule

A tool is an enterprise contract, not just a function exposed to an LLM.
