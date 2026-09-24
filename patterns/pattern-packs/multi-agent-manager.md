# Pack — Multi-Agent Manager

## Intent

Use a central orchestrator agent that delegates bounded tasks to specialist agents while retaining overall control and synthesis.

## Use when

- specialists require separate prompts/context/tools;
- one agent suffers tool or instruction overload;
- security boundaries map naturally to specialists;
- central synthesis is required.

## Structure

```text
User
 ↓
Manager
 ├─ Specialist A
 ├─ Specialist B
 └─ Specialist C
 ↓
Synthesis
```

Specialists should expose narrow contracts and may be called as tools.

## FAST
- at most 2–3 specialists;
- obvious routing;
- no unnecessary nesting.

## MVP
- specialist contracts;
- routing evals;
- bounded delegation;
- trace evaluation;
- failure fallback.

## PRODUCT
- per-agent permissions;
- budgets/turn limits;
- end-to-end trace grading;
- loop protection;
- observability by agent and outcome.

## Key rule

Multi-agent is justified by separation needs, not by novelty.
