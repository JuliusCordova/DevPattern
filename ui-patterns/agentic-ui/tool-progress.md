# Tool Progress Pattern

## Intent

Expose meaningful progress while an agent uses tools or executes multi-step work.

## Show

- current meaningful step;
- waiting state;
- recoverable failure;
- approval needed;
- completion.

Do not expose raw chain-of-thought or low-value internal reasoning.

## Example

```text
Checking customer data
   ↓
Validating pricing rules
   ↓
Calculating scenarios
   ↓
Preparing recommendation
```

## Key rule

> Show useful operational progress, not hidden model reasoning.
