# Pack — Sandboxed Code Execution

## Intent

Allow an agent to generate and execute code in an isolated environment for analysis, transformation, testing, or artifact creation.

## Use when

- data analysis requires iterative code;
- files must be transformed;
- computation is easier and more reliable in code than natural language;
- the agent must test generated logic.

## Avoid when

- a deterministic service already provides the result;
- arbitrary code adds unnecessary security risk.

## Structure

```text
Agent
  ↓
Code Plan
  ↓
Sandbox
  ↓
Execute
  ↓
Output / Files / Errors
  ↓
Agent validates result
```

## FAST
- managed sandbox;
- synthetic files/data;
- strict execution limits.

## MVP
- persistent sandbox per task where useful;
- time/memory limits;
- dependency policy;
- output validation;
- execution traces.

## PRODUCT
- strong process isolation;
- network restrictions;
- allow/deny dependency policy;
- malware/data-exfiltration controls;
- artifact provenance;
- retention cleanup;
- resource/cost limits.

## GCP note

ADK supports Agent Runtime Code Execution using isolated sandboxes with persistent task state across calls.

## Key rule

> Generated code must execute in a sandbox, never directly inside the application runtime.
