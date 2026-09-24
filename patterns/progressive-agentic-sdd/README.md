# PA-SDD — Progressive Agentic Spec-Driven Development

**PA-SDD** is a progressive engineering pattern for building modern software and agentic products with high development speed at the beginning and increasing assurance as the product matures.

> **Minimum ceremony. Maximum evidence.**

## Problem

Classic software delivery often starts coding too early.

Heavyweight SDD approaches solve that problem but can introduce too much ceremony for demos, PoCs, and rapid discovery.

PA-SDD resolves the tension by separating **engineering rigor from documentation volume**.

## Core equation

```text
PA-SDD =
  Spec-Driven
+ Pattern-Driven
+ Architecture-Driven
+ Eval-Driven
+ Evidence-Driven
```

Architecture-Driven does **not** mean designing a large architecture before coding. It means reusing proven architectural patterns and introducing boundaries only when they protect delivery speed, testability, integrations, security, or future change.

## Progressive lifecycle

```text
IDEA
 │
 ▼
FAST DEMO
 │  mini spec
 │  simple feature slice
 │  happy path
 │  acceptance
 │  smoke
 ▼
MVP
 │  architecture where justified
 │  contracts
 │  golden evals
 │  automated evidence
 ▼
PRODUCT
    stronger boundaries
    security
    NFR
    observability
    adversarial evals
    promotion gates
    rollback
    operations
```

A product should not be forced to satisfy PRODUCT-level controls before its value proposition has been validated.

## Engineering flow

```text
Business Intent
      ↓
Minimum Sufficient Spec
      ↓
Pattern Selection
      ↓
Architecture Decision
      ↓
Contracts + Evals
      ↓
Implementation
      ↓
Executable Evidence
      ↓
Promotion Gate
      ↓
Operate
      ↓
Learn
      ↓
Evolve Spec
```

## Five foundations

### Spec-Driven
The specification captures desired behavior before implementation details.

### Pattern-Driven
Reusable patterns encode engineering decisions that should not be rediscovered in every project.

### Architecture-Driven
Architecture is selected progressively. PA-SDD prefers simple feature slices first and introduces Hexagonal Slice boundaries only where they create concrete value.

### Eval-Driven
Agent behavior is validated against representative scenarios, tools, traces, guardrails, and business expectations.

### Evidence-Driven
Promotion decisions rely on machine-generated evidence wherever possible.

## Architecture principle

> **Start simple. Add boundaries only when they protect something valuable.**

Recommended progression:

```text
FAST DEMO     → Simple Feature Slice
MVP      → Simple Slice or Hexagonal Slice where justified
PRODUCT  → Hexagonal Slice preferred for critical capabilities
```

Hexagonal + Vertical Slice is a preferred pattern for products with meaningful domain logic, multiple integrations, tool-calling agents, vendor dependencies, or higher operational risk. It is not mandatory for every feature.

See [Architecture Patterns](../architecture/README.md).

## Core principle

> **Rigor grows with risk and product maturity, not with lines of code.**

See:
- [Lifecycle](lifecycle.md)
- [Maturity Model](maturity-model.md)
- [Decision Framework](decision-framework.md)
