# Feedback States Pattern

Every meaningful interaction should define its visible state.

## Minimum state model

```text
IDLE
 ↓
LOADING / PROCESSING
 ├─→ SUCCESS
 ├─→ WARNING
 └─→ ERROR → RETRY / RECOVER
```

For long-running work add:
- queued;
- running;
- waiting-for-user;
- waiting-for-system;
- cancelled;
- partially-completed.

## Key rule

> Silence is not a valid system state.
