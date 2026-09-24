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
Component Architecture Profile
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

## Component Architecture Profiles

Architecture patterns and Pattern Packs remain vendor-neutral.

**Component Architecture Profiles** map those patterns into current managed services for:

- Azure
- Microsoft Fabric
- GCP
- AWS

```text
Definition
   ↓
Architecture Pattern
   ↓
Pattern Packs
   ↓
Component Architecture Profile
   ↓
Implementation
```

Cloud recommendations are living artifacts and are reviewed **weekly** because managed services, agent runtimes, limits, pricing, integrations and reference architectures evolve continuously.

A weekly review does not automatically change the baseline. Recommendations change only when there is evidence of material improvement.

Lifecycle status:
- CURRENT
- REVIEW_REQUIRED
- DEPRECATED
- REPLACED

Evidence level:
- OFFICIAL
- PROVEN
- EXPERIMENTAL

See [Component Architecture Profiles](component-profiles/README.md).

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
│   ├── architecture/
│   ├── pattern-packs/
│   └── implementation-profiles/
├── component-profiles/
│   ├── azure/
│   ├── fabric/
│   ├── gcp/
│   └── aws/
└── schemas/
```

## Guiding principle

> The artifact, abstraction, or managed component exists only if it reduces ambiguity, risk, rework, operational uncertainty, or future change cost.

PA-SDD is intentionally framework-neutral and cloud-neutral at the pattern level.

## Status

**v0.3 — Component Architecture Profiles**

This version adds governed, weekly-reviewed cloud component mappings while preserving the principle of progressive architecture from FAST DEMO to PRODUCT.
