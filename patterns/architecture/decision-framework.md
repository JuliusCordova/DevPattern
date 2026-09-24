# Architecture Decision Framework

PA-SDD uses progressive architecture selection.

## Step 1 — Start with the simplest viable structure

Use **Simple Feature Slice** when most of these are true:

- FAST demo or discovery;
- limited business logic;
- one implementation of each dependency;
- few external integrations;
- low operational risk;
- short expected lifetime;
- architecture can still be changed cheaply.

## Step 2 — Introduce Hexagonal Slice when boundaries matter

Prefer **Hexagonal Slice Architecture** when one or more of these become material:

- multiple external systems;
- meaningful domain rules;
- LLM/provider independence;
- several tools or agent capabilities;
- testability without infrastructure;
- permission or security boundaries;
- independent feature evolution;
- likely technology replacement;
- production operational requirements.

## Step 3 — Avoid automatic escalation

The transition is not:

```text
FAST → MVP → PRODUCT
  = more folders automatically
```

It is:

```text
Product maturity
      +
Risk
      +
Integration complexity
      +
Change pressure
      ↓
Justified architectural boundaries
```

## Suggested default

```text
FAST
  ↓
Simple Feature Slice

MVP
  ↓
Simple Slice
or
Hexagonal Slice where justified

PRODUCT
  ↓
Hexagonal Slice preferred
for important capabilities
```

Different slices inside the same product may use different levels of structure.
