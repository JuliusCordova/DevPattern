# Pack — Single Agent

## Intent

Use one agent with instructions, model, tools, guardrails, and explicit exit conditions.

OpenAI recommends maximizing a single agent before introducing multi-agent orchestration because it keeps evaluation and maintenance simpler.

## Use when

- one coherent responsibility exists;
- the agent can reliably select among its tools;
- instructions remain understandable;
- a single context is sufficient.

## Escalate when

Consider multi-agent only when:
- logic becomes difficult to express;
- tool overlap causes persistent selection errors;
- context/security boundaries require separation;
- specialist ownership materially improves quality.

## Contract

```yaml
agent:
  purpose:
  inputs:
  outputs:
  tools:
  forbidden_actions:
  exit_conditions:
  max_turns:
  evals:
```

## FAST
- one agent;
- minimal tools;
- bounded run;
- basic smoke scenarios.

## MVP
- agent contract;
- golden evals;
- tool-call evals;
- retries and limits;
- tracing.

## PRODUCT
- guardrails;
- risk-based tool permissions;
- production evals;
- cost/latency SLOs;
- fallback and escalation.

## Key rule

Single agent is the default agentic pattern.
