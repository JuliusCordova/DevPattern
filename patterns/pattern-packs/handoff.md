# Pack — Handoff

## Intent

Transfer ownership of the interaction or workflow from one specialist agent to another.

## Use when

- different specialists should directly own different stages;
- user interaction continues with the receiving specialist;
- centralized synthesis is unnecessary.

## Avoid when

Use Multi-Agent Manager when one orchestrator must maintain global control.

## Structure

```text
User
 ↓
Agent A
 ├─ handles request
 └─ HANDOFF
       ↓
     Agent B
       ↓
     User
```

## FAST DEMO
- explicit handoff conditions;
- 2 agents maximum where practical.

## MVP
- handoff contract;
- context-transfer policy;
- loop prevention;
- routing evals.

## PRODUCT
- permission/context minimization;
- traceability;
- failed-handoff recovery;
- bounded handoff count.

## Key rule

Transfer only the context the receiving agent actually needs.
