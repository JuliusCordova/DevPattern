# Pack — Human-in-the-Loop

## Intent

Pause or redirect agent execution when human judgment or authorization is required.

## Triggers

- high-risk or irreversible action;
- financial/legal impact;
- low model confidence where confidence is meaningful;
- repeated failure/retry threshold;
- policy exception;
- missing information requiring judgment.

## Patterns

```text
Agent → Proposed Action → Human Approve/Reject → Execute
```

or

```text
Agent → Need More Information → Human/User → Resume
```

## FAST DEMO
- manual confirmation before sensitive action.

## MVP
- explicit approval state;
- resumable workflow;
- approval audit.

## PRODUCT
- durable checkpoints;
- approver authorization;
- segregation of duties;
- timeout/escalation;
- immutable evidence.

## Key rule

Human approval is a control boundary, not a chat message saying "Are you sure?".
