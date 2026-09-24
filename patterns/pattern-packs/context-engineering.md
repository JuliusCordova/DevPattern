# Pack — Context Engineering

## Intent

Engineer the minimum high-quality context an agent needs at each step rather than continuously expanding the prompt.

## Context sources

- system/developer instructions;
- current user request;
- session state;
- retrieved knowledge;
- semantic metadata;
- tool results;
- memory;
- policies;
- prior artifacts.

## Reference flow

```text
Task
 ↓
Context Need
 ↓
Select / Retrieve
 ↓
Filter by Permissions
 ↓
Compress / Structure
 ↓
Model
 ↓
Persist only useful state
```

## Practices

- separate durable instructions from task-specific context;
- retrieve only what is relevant;
- prefer structured context over uncontrolled text;
- version prompts/instructions;
- prevent untrusted retrieved text from becoming executable policy;
- summarize long histories;
- treat context size, latency and cost as architecture metrics.

## FAST
- concise instructions;
- no unnecessary memory;
- manual context.

## MVP
- context assembly function;
- metadata filters;
- prompt/version tracking;
- token budget;
- eval context changes.

## PRODUCT
- permission-aware context;
- injection boundaries;
- context provenance;
- dynamic compression;
- cache strategy;
- cost/quality optimization.

## Key rule

> More context is not necessarily better context.
