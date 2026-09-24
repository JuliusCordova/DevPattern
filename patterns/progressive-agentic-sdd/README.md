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
+ Eval-Driven
+ Evidence-Driven
```

## Progressive lifecycle

```text
IDEA
 │
 ▼
FAST
 │  mini spec
 │  happy path
 │  acceptance
 │  smoke
 ▼
MVP
 │  architecture
 │  contracts
 │  golden evals
 │  automated evidence
 ▼
PRODUCT
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
Architecture + Contracts + Evals
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

## Four foundations

### Spec-Driven
The specification captures desired behavior before implementation details.

### Pattern-Driven
Reusable patterns encode engineering decisions that should not be rediscovered in every project.

### Eval-Driven
Agent behavior is validated against representative scenarios, tools, traces, guardrails, and business expectations.

### Evidence-Driven
Promotion decisions rely on machine-generated evidence wherever possible.

## Core principle

> **Rigor grows with risk and product maturity, not with lines of code.**

See:
- [Lifecycle](lifecycle.md)
- [Maturity Model](maturity-model.md)
- [Decision Framework](decision-framework.md)
