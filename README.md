# DevPattern

**DevPattern** is a practical engineering pattern library for accelerating modern software and agentic product development without turning delivery into a documentation-heavy process.

Its first pattern is **PA-SDD — Progressive Agentic Spec-Driven Development**.

> **Minimum ceremony. Maximum evidence.**

PA-SDD combines four complementary ideas:

- **Spec-Driven** — build from explicit intent and acceptance criteria.
- **Pattern-Driven** — reuse proven engineering and agentic patterns instead of redefining them in every project.
- **Eval-Driven** — define how agent behavior will be evaluated before relying on it.
- **Evidence-Driven** — promote software based on executable evidence, not documentation alone.

## Why PA-SDD?

Traditional SDD can become too heavy for demos and early experimentation. PA-SDD keeps the same discipline but applies it progressively:

```text
IDEA
 │
 ▼
FAST
 │   Minimum sufficient specification
 │   Working demo + smoke validation
 ▼
MVP
 │   Architecture + contracts + golden evals
 │   Automated evidence
 ▼
PRODUCT
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
Architecture / Contracts / Evals
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

## Development modes

| Mode | Goal | Required discipline |
|---|---|---|
| **FAST** | Demo, discovery, PoC | Mini Spec + acceptance + smoke |
| **MVP** | Validatable product | Spec + architecture + contracts + golden evals + evidence |
| **PRODUCT** | Production workload | Full risk controls + security + NFR + observability + promotion gates |

See [PA-SDD](patterns/progressive-agentic-sdd/README.md) for the complete pattern.

## Repository structure

```text
DevPattern/
├── constitution/
├── patterns/
│   └── progressive-agentic-sdd/
├── templates/
│   ├── fast/
│   ├── mvp/
│   └── product/
└── schemas/
```

## Guiding principle

> The artifact exists only if it reduces ambiguity, risk, rework, or operational uncertainty.

PA-SDD is intentionally framework-neutral. It can be implemented using Google ADK, Microsoft Agent Framework, OpenAI Agents SDK, LangGraph, custom runtimes, or conventional application stacks.

## Status

**v0.1 — Foundation**

This version defines the core philosophy, lifecycle, maturity model, minimum templates, and agent/tool contracts.
