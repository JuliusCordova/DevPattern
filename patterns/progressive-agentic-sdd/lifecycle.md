# PA-SDD Lifecycle

## Stage 0 — Intent

Define:
- business outcome
- target user
- problem to solve
- why AI or an agent may be useful
- success signal

## Stage 1 — Minimum Sufficient Spec

Capture only what is necessary to start safely:
- goal
- user
- main scenario
- acceptance criteria
- explicit out-of-scope items
- key constraints

## Stage 2 — Pattern Selection

Select reusable patterns such as:
- Web Application
- API
- Single Agent
- Tool Calling
- RAG
- Human Approval
- Multi-Agent
- Governed Agent

## Stage 3 — Architecture Decision

Choose the **simplest structure that protects the next stage of delivery**.

Typical progression:

```text
FAST DEMO     → Simple Feature Slice
MVP      → Simple Slice or Hexagonal Slice where justified
PRODUCT  → Hexagonal Slice preferred for critical capabilities
```

Do not introduce ports, adapters, interfaces, or extra layers automatically. Add them when they materially improve testability, isolate volatile dependencies, protect business logic, enforce security boundaries, or reduce future change cost.

## Stage 4 — Contracts

Added progressively when needed:
- agent contract
- tool contracts
- data contracts
- permission model
- external integration contracts

## Stage 5 — Evals

Define expected behavior before trusting the implementation:
- happy-path cases
- edge cases
- tool-selection expectations
- forbidden actions
- groundedness or correctness criteria
- business-level acceptance

## Stage 6 — Build

Implementation should remain traceable to the spec, selected patterns, and chosen architecture.

## Stage 7 — Evidence

Collect:
- unit tests
- integration tests
- eval results
- security checks
- smoke tests
- latency and cost data where relevant

## Stage 8 — Promotion

Promotion is proportional to maturity:

```text
FAST DEMO     → Demo acceptance
MVP      → Evidence gate
PRODUCT  → Production promotion gate
```

## Stage 9 — Observe

Measure:
- business outcome
- task completion
- agent behavior
- tool use
- errors
- latency
- cost per successful outcome

## Stage 10 — Evolve

Important findings update the specification, patterns, architecture, tests, and evals.

```text
Failure
  ↓
Root cause
  ↓
Spec / Pattern / Architecture update
  ↓
New test or eval
  ↓
Regression protection
```
