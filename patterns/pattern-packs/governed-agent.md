# Pack — Governed / Permission-Aware Agent

## Intent

Apply enterprise authorization, data governance, audit, and runtime safety controls to agentic systems.

## Core principle

The orchestrator must never gain broader access than the user and delegated capabilities allow.

## Capabilities

- authenticated identity;
- authorization before retrieval and action;
- permission-aware RAG;
- least-privilege tools;
- data classification;
- guardrails;
- audit/logging;
- policy enforcement;
- human approval for high-risk actions.

## Reference model

```text
User Identity
     ↓
Authorization Context
     ↓
Agent
 ├─ Knowledge retrieval filtered by permissions
 ├─ Tools filtered by permissions
 └─ High-risk actions → approval
     ↓
Audit Evidence
```

## FAST DEMO
- synthetic/non-sensitive data preferred;
- explicit prohibited actions.

## MVP
- real identity propagation;
- tool permissions;
- retrieval filters;
- audit traces.

## PRODUCT
- policy-as-code where practical;
- segregation of duties;
- DLP/data controls;
- prompt-injection defenses;
- scoped credentials;
- immutable audit evidence;
- security/adversarial evals.

## Key rule

Permission enforcement belongs in deterministic controls and data/tool layers, not only in prompts.
