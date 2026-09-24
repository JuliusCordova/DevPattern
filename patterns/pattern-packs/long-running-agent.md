# Pack — Long-Running Agent

## Intent

Support tasks that exceed a normal synchronous request and require durable progress, resume, cancellation, or asynchronous result retrieval.

## Use when

- work can last minutes or hours;
- external approvals interrupt execution;
- large research/data processing tasks need progress tracking;
- clients may disconnect before completion.

## Structure

```text
Start Task
   ↓
Durable Task State
   ↓
Work / Checkpoint
   ↓
Wait / Resume / Retry
   ↓
Artifact / Result
```

## FAST
- avoid durable orchestration if a normal request is sufficient.

## MVP
- task ID;
- status lifecycle;
- timeout/cancel;
- persisted checkpoints;
- resumability.

## PRODUCT
- durable execution state;
- replay-safe steps;
- idempotent writes;
- human approval checkpoints;
- asynchronous notifications;
- retention and audit.

## Protocol options

- MCP Tasks for MCP-based long-running tool calls.
- A2A Tasks for remote agent collaboration.
- Cloud Run Jobs for run-to-completion workloads.
- workflow/orchestration engine only when durable coordination is genuinely required.

## Key rule

> A long prompt is not a long-running architecture; durability must be explicit.
