# GCP Proven Practices from Reference Projects

This document captures patterns extracted from implementations already exercised in the reference repositories.

## 1. Controlled Cloud Run promotion

ATLAS DataGob established a useful delivery flow:

```text
Build
 ↓
Deploy candidate
 ↓
Smoke
 ↓
Authenticated smoke
 ↓
Collect evidence
 ↓
Promotion gate
 ↓
Go / Conditional Go / No-Go
```

This is the preferred PA-SDD pattern for MVP → PRODUCT promotion on GCP.

## 2. Candidate service before production

Business Rules Silver validates a candidate Cloud Run service before promotion.

The pipeline pattern is:

```text
Tests
 ↓
Build candidate image
 ↓
Push Artifact Registry
 ↓
Deploy test/candidate service
 ↓
Run real agent/API smoke
 ↓
Validate telemetry/evidence
 ↓
Promote
```

This is preferable to deploying directly to the production service.

## 3. Validate business outcome, not infrastructure status

Business Rules Silver exposed an important lesson:

```text
Dataproc SUCCEEDED
       ≠
Business outcome validated
```

The correct acceptance pattern is:

```text
Technical execution succeeded
        +
Post-execution business validation passed
        =
Successful outcome
```

PA-SDD therefore requires evidence at the **outcome level**, not only infrastructure health.

## 4. Idempotency is a production requirement

Repeated execution exposed duplicate Silver records.

Reusable rule:

> Any action/tool that writes state and may be retried must define idempotency or deterministic deduplication semantics.

Examples:
- MERGE by business key;
- request/run id;
- idempotency key;
- deterministic upsert;
- duplicate detection.

## 5. Separate agent reasoning from deterministic computation

PricingPrima formalizes:

```text
LLM:
- understand intent
- choose tools
- orchestrate
- explain trade-offs

Deterministic services:
- calculate margin
- probabilities
- simulations
- optimization
- risk metrics
- business constraints
```

This becomes a core PA-SDD rule for high-value decisions.

## 6. Contract-first data and APIs

PricingPrima uses explicit JSON schemas for request/result/scenario/risk contracts.

ATLAS DataGob validates API and canonical data artifacts before execution.

Reusable pattern:

```text
Spec
 ↓
Contract
 ↓
Implementation
 ↓
Contract Test
 ↓
Runtime
```

## 7. Runtime provenance is evidence

Business Rules Silver demonstrated that source provenance must be verified from the deployed Cloud Run revision/image/build rather than assumed from a repository path.

Production evidence should capture:

- Git SHA;
- container image digest/tag;
- Cloud Build ID;
- Cloud Run revision;
- configuration version;
- model/prompt version when relevant.

## 8. AgentOps + FinOps belong in the product

Business Rules Silver validates:
- agent runs;
- active/completed/failed executions;
- duration;
- LLM calls;
- tokens;
- billing availability;
- service-level cost semantics.

PA-SDD recommendation:

At MVP start with:
- run count;
- errors;
- duration;
- model/tokens.

At PRODUCT add:
- cost per successful outcome;
- cost by capability/service;
- budget thresholds;
- outcome-to-cost traceability.

## 9. Synthetic data for FAST DEMO/MVP demos

ATLAS DataGob and PricingPrima both demonstrate the value of:
- curated synthetic datasets;
- deterministic reset/seed;
- repeatable demo state.

Reusable rule:

> A demo should be resettable and repeatable before it is realistic.

## 10. Human approval before consequential publication

PricingPrima keeps pricing recommendation separate from publication.

Pattern:

```text
Agent recommendation
      ↓
Deterministic validation
      ↓
Human approval
      ↓
Execution / publication
```

Use this by default for financial, operational, regulated, or irreversible decisions.
