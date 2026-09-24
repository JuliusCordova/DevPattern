# Agentic UI Patterns

Agentic interfaces require interaction patterns beyond a traditional chat window.

## Baseline capabilities

When relevant, expose:

- current agent status;
- tool/action progress;
- sources/citations;
- distinction between answer, recommendation and action;
- approval checkpoints;
- recoverable errors;
- handoff or escalation;
- uncertainty where material.

## Reference interaction

```text
User Request
   ↓
Agent Understanding
   ↓
Visible Processing / Tool Progress
   ↓
Grounded Result
   ↓
Sources / Evidence
   ↓
Approval if consequential
   ↓
Execution
   ↓
Outcome Evidence
```

## Key rule

> The user should know whether the agent is thinking, retrieving, recommending, waiting, or acting.
