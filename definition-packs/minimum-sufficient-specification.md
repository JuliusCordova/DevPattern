# Minimum Sufficient Specification (MSS)

The MSS is the default Definition Pack for software and agentic products.

It defines the minimum product information required before architecture, Pattern Packs, UI patterns and cloud components are selected.

## Core sections

1. Business Intent
2. Scope
3. Out of Scope
4. Actors / Personas
5. User Stories
6. Functional Requirements
7. Non-Functional Requirements
8. Acceptance Criteria
9. Business Rules
10. Logical Data Model
11. Integrations
12. Edge Cases
13. Success Metrics

## FAST DEMO

Minimum expected:

- problem / business intent;
- target user;
- 3–5 critical user stories;
- key functional requirements;
- acceptance criteria for the main flow;
- minimum logical data model when persistence exists;
- explicit out of scope;
- one measurable success criterion.

The default artifact may be a single `SPEC.md`.

## MVP

Add:

- complete prioritized user stories;
- functional requirements;
- relevant non-functional requirements;
- business rules;
- logical data model;
- integration contracts;
- edge cases;
- traceability;
- testable acceptance criteria;
- success metrics;
- security/data assumptions where relevant.

## PRODUCT

Add only when required:

- identity and authorization model;
- privacy/data classification;
- RPO/RTO;
- resilience requirements;
- compliance;
- threat model;
- observability requirements;
- operational support criteria;
- DR/recovery;
- audit requirements;
- capacity and cost constraints.

## User Stories

Use independently testable stories where practical.

```text
US-001

As a <user>
I want <capability>
so that <outcome>
```

## Functional Requirements

Functional requirements describe system behavior.

```text
FR-001
The system shall allow an authenticated requester to create an initiative.
```

Requirements should be clear, testable and traceable.

## Non-Functional Requirements

Only add NFRs that materially affect design.

Typical categories:

- performance;
- availability;
- security;
- privacy;
- scalability;
- accessibility;
- observability;
- maintainability;
- interoperability;
- cost.

## Acceptance Criteria

Acceptance criteria bridge product intent and executable evidence.

```gherkin
Given an authenticated user
When the user submits all required fields
Then the record is created
And a unique identifier is returned
And the initial state is DRAFT
```

## Business Rules

Business rules must not be buried only in code, prompts, SQL, or UI logic.

```text
BR-001
High-risk initiatives require strategic committee review.
```

## Logical Data Model

FAST DEMO may use a compact logical model.

```text
User
  │
  └──< Initiative
          ├──< Assessment
          └──< Decision
```

For each relevant entity capture:

- identifier;
- key attributes;
- relationships;
- ownership;
- sensitivity/classification where material;
- lifecycle/retention where material.

## Integrations

Document purpose and direction before technology detail.

```yaml
integration:
  id: jira
  direction: outbound
  purpose: create_delivery_item
```

## Edge Cases

At minimum consider:

- missing information;
- duplicate records;
- authorization failure;
- unavailable dependency;
- timeout;
- cancellation;
- partial completion;
- invalid external response.

## Traceability

When useful:

```text
BUS-001
  ↓
US-003
  ↓
FR-008
  ↓
BR-004
  ↓
AC-012
  ↓
TEST-019
  ↓
EVIDENCE
```

## Agentic extension

If the solution is agentic, extend MSS with:

- Agent Contract;
- Tool Contracts;
- knowledge strategy;
- context strategy;
- memory strategy;
- permissions;
- human approval rules;
- evals;
- observability;
- runtime limits.

## Key rule

> Build from a definition that is sufficient to test and evolve — not from assumptions hidden inside implementation.
