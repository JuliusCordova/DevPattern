# Pack — Event-Driven Agent

## Intent

Trigger agentic behavior from business or platform events rather than synchronous user requests.

## Use when

- new data, messages, files, alerts, or state changes should trigger action;
- work should be decoupled from a UI request;
- bursts need buffering;
- producer and agent lifecycle should be independent.

## Structure

```text
Event Source
    ↓
Topic / Event Bus
    ↓
Event Router
    ↓
Agent / Workflow
    ↓
Tool / Domain Action
    ↓
Outcome Event + Evidence
```

## FAST
- one topic/event;
- one consumer;
- synthetic events;
- basic deduplication.

## MVP
- event schema;
- correlation/run ID;
- retry + dead-letter handling;
- idempotency;
- outcome evidence.

## PRODUCT
- versioned event contracts;
- replay strategy;
- DLQ/runbook;
- ordering guarantees where required;
- least-privilege identities;
- distributed tracing;
- SLOs.

## GCP default

Pub/Sub + Eventarc + Cloud Run is the preferred simple path for event-triggered services. Use Worker Pools only for background fleet behavior that justifies them.

## Key rule

> Event delivery success is not business outcome success; validate both.
