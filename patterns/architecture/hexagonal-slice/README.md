# Hexagonal Slice Architecture

**Hexagonal Slice Architecture** combines two complementary ideas:

- **Vertical Slice Architecture** organizes software around business capabilities or features.
- **Hexagonal Architecture (Ports & Adapters)** protects core application and domain behavior from external technologies.

The result is a feature-oriented architecture designed to keep changes localized while preserving clean integration boundaries.

## Why combine them?

Traditional horizontal layering often spreads one feature across many folders:

```text
controllers/
services/
repositories/
domain/
infrastructure/
```

A vertical slice keeps a capability together:

```text
features/
  pricing/
  customer/
  approval/
```

Hexagonal boundaries are then introduced inside a slice only when they add value.

```text
Feature / Slice
      │
      ▼
Driving Adapter
 UI / API / Event / Agent
      │
      ▼
Application / Use Case
      │
      ▼
Domain Logic
      │
      ▼
Outbound Port
      │
      ▼
Driven Adapter
 DB / API / Queue / LLM / Tool
```

## Agentic principle

The agent is normally an orchestrator or driving adapter.

Critical business logic should not live only inside prompts.

```text
Agent
  │
  ▼
Use Case
  │
  ▼
Domain Capability
  │
  ├── Customer Port
  ├── Pricing Port
  └── Approval Port
```

This lets LLM providers, databases, APIs, vector stores, and other technologies remain replaceable adapters.

## Progressive application

### FAST

Keep the structure intentionally small.

```text
feature/
├── app.py
├── agent.py
├── tools.py
└── tests/
```

Use conceptual boundaries without creating unnecessary interfaces.

### MVP

Introduce explicit boundaries where integration and testing justify them.

```text
feature/
├── application/
├── ports/
├── adapters/
├── agent/
└── evals/
```

### PRODUCT

Use stronger boundaries when required by risk, scale, security, or operational complexity.

```text
feature/
├── domain/
├── application/
├── ports/
│   ├── inbound/
│   └── outbound/
├── adapters/
│   ├── inbound/
│   └── outbound/
├── agent/
├── tools/
├── policies/
├── evals/
└── observability/
```

## Dependency rules

1. Domain code does not depend on adapters.
2. Application logic does not depend directly on vendor SDKs.
3. External systems are accessed through explicit boundaries when isolation adds value.
4. Adapters implement those boundaries.
5. A feature owns its behavior end-to-end whenever practical.
6. Cross-feature dependencies use explicit contracts.
7. Agents orchestrate capabilities; they do not replace critical business rules.
8. LLM providers and vector stores are infrastructure dependencies.
9. Prompts and agent instructions are versioned engineering assets.
10. A slice owns its tests and relevant evals.
11. Prefer composition over unnecessary abstraction.
12. Do not introduce a port or interface without a concrete reason.

## Core rule

> Architecture grows when it protects delivery speed, testability, integration boundaries, security, or change — not because a diagram looks cleaner.
