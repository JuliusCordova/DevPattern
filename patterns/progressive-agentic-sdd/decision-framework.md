# PA-SDD Decision Framework

Use this sequence before increasing delivery ceremony or architecture complexity.

## 1. Is the problem deterministic?

If yes, prefer conventional software or workflow automation.

If no, continue.

## 2. Does an LLM materially improve the outcome?

If no, avoid introducing an agent.

If yes, continue.

## 3. Is dynamic tool selection or multi-step reasoning required?

If no, prefer an AI-assisted workflow.

If yes, a single agent may be justified.

## 4. Is multi-agent complexity really needed?

Use multiple agents only when specialization, context isolation, permission boundaries, scale, or orchestration complexity justify it.

## 5. What delivery mode is appropriate?

```text
Need to prove the idea quickly?
        ↓
      FAST

Need repeatable validation and measurable behavior?
        ↓
      MVP

Need operational reliability, governance and controlled promotion?
        ↓
    PRODUCT
```

## 6. What architecture is appropriate?

```text
Can a simple feature slice remain clear and testable?
        │
       YES
        ▼
Keep it simple
        │
       NO
        ▼
Introduce justified boundaries
        │
        ▼
Hexagonal Slice
```

## Final test

Before adding any artifact, interface, port, adapter, service, agent, or additional layer, ask:

> What concrete ambiguity, risk, dependency, testability problem, security boundary, or future change does this remove?

If there is no clear answer, do not add it yet.
