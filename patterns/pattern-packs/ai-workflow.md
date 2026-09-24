# Pack — AI Workflow

## Intent

Use an LLM inside an explicit workflow where the developer controls the execution path.

## Use when

- process steps are known;
- predictability matters more than autonomy;
- branching can be expressed deterministically;
- human approvals or checkpoints occur at known stages.

## Avoid when

Use a Single Agent instead when the model must dynamically decide what to do next.

## Reference structure

```text
Input
  ↓
Validate
  ↓
LLM Step
  ↓
Deterministic Logic
  ↓
Tool / API
  ↓
Optional Approval
  ↓
Output
```

## FAST DEMO
- one happy-path workflow;
- basic validation;
- smoke test.

## MVP
- explicit state;
- retries/timeouts;
- observable steps;
- integration tests.

## PRODUCT
- checkpoints/resume;
- idempotency;
- failure handling;
- HITL gates;
- end-to-end evidence.

## Key rule

Prefer workflows over agents when the path is known.
