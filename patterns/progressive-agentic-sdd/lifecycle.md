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

## Stage 3 — Architecture and Contracts

Added progressively when needed:
- architecture decisions
- agent contract
- tool contracts
- data contracts
- permission model
- external integration contracts

## Stage 4 — Evals

Define expected behavior before trusting the implementation:
- happy-path cases
- edge cases
- tool-selection expectations
- forbidden actions
- groundedness or correctness criteria
- business-level acceptance

## Stage 5 — Build

Implementation should remain traceable to the spec and selected patterns.

## Stage 6 — Evidence

Collect:
- unit tests
- integration tests
- eval results
- security checks
- smoke tests
- latency and cost data where relevant

## Stage 7 — Promotion

Promotion is proportional to maturity:

```text
FAST     → Demo acceptance
MVP      → Evidence gate
PRODUCT  → Production promotion gate
```

## Stage 8 — Observe

Measure:
- business outcome
- task completion
- agent behavior
- tool use
- errors
- latency
- cost per successful outcome

## Stage 9 — Evolve

Important findings update the specification, patterns, tests, and evals.

```text
Failure
  ↓
Root cause
  ↓
Spec / Pattern update
  ↓
New test or eval
  ↓
Regression protection
```
