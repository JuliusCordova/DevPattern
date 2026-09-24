# DevPattern

**DevPattern** is a practical engineering pattern library for accelerating modern software and agentic product development without turning delivery into a documentation-heavy process.

Its first pattern is **PA-SDD — Progressive Agentic Spec-Driven Development**.

> **Minimum ceremony. Maximum evidence.**

PA-SDD combines five complementary ideas:

- **Spec-Driven** — build from explicit intent and acceptance criteria.
- **Pattern-Driven** — reuse proven engineering and agentic patterns instead of redefining them in every project.
- **Architecture-Driven** — select the simplest viable architecture and add boundaries only when they create concrete value.
- **Eval-Driven** — define how agent behavior will be evaluated before relying on it.
- **Evidence-Driven** — promote software based on executable evidence, not documentation alone.

## Why PA-SDD?

Traditional SDD can become too heavy for demos and early experimentation. PA-SDD keeps the same discipline but applies it progressively:

```text
IDEA
 │
 ▼
FAST DEMO
 │   Minimum sufficient specification
 │   Simple feature slice
 │   Working demo + smoke validation
 ▼
MVP
 │   Architecture where justified
 │   Contracts + golden evals
 │   Automated evidence
 ▼
PRODUCT
     Stronger architecture boundaries
     Security + NFR + observability
     Promotion gates + rollback + operations
```

The rigor grows with **risk and product maturity**, not with the number of lines of code.

## Core lifecycle

```text
Business Intent
      ↓
Minimum Sufficient Spec
      ↓
Reusable Patterns
      ↓
Architecture Decision
      ↓
Contracts / Evals
      ↓
Implementation
      ↓
Executable Evidence
      ↓
Promotion
      ↓
Observe
      ↓
Evolve the Spec
```

## Architecture approach

DevPattern prefers **simple feature slices first**.

When domain complexity, integrations, vendor dependencies, testability, security, or operational risk justify stronger boundaries, the preferred pattern is **Hexagonal Slice Architecture**: Vertical Slice + Ports & Adapters.

> Architecture grows when it protects delivery speed, testability, integration boundaries, security, or change — not because a diagram looks cleaner.

See [Architecture Patterns](patterns/architecture/README.md).

## Development modes

| Mode | Goal | Required discipline |
|---|---|---|
| **FAST DEMO** | Demo, discovery, PoC | Mini Spec + simple slice + acceptance + smoke |
| **MVP** | Validatable product | Spec + justified architecture + contracts + golden evals + evidence |
| **PRODUCT** | Production workload | Stronger boundaries + full risk controls + security + NFR + observability + promotion gates |

See [PA-SDD](patterns/progressive-agentic-sdd/README.md) for the complete pattern.

## Repository structure

```text
DevPattern/
├── constitution/
├── patterns/
│   ├── progressive-agentic-sdd/
│   └── architecture/
│       └── hexagonal-slice/
├── templates/
│   ├── fast/
│   ├── mvp/
│   └── product/
└── schemas/
```

## Guiding principle

> The artifact or abstraction exists only if it reduces ambiguity, risk, rework, operational uncertainty, or future change cost.

PA-SDD is intentionally framework-neutral. It can be implemented using Google ADK, Microsoft Agent Framework, OpenAI Agents SDK, LangGraph, custom runtimes, or conventional application stacks.

## Status

**v0.1 — Foundation**

This version defines the core philosophy, lifecycle, progressive architecture approach, and the initial Hexagonal Slice pattern.
