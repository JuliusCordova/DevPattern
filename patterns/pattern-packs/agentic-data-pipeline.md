# Pack — Agentic Data Pipeline

## Intent

Use agents to assist in data engineering tasks while keeping execution, quality, lineage, and data contracts deterministic and governable.

## Use when

- agents can accelerate profiling, mapping, rule generation, pipeline troubleshooting, or artifact generation;
- human/data engineer judgment remains valuable;
- generated transformations can be validated before execution.

## Reference flow

```text
Source Discovery
   ↓
Profiler Agent
   ↓
Mapping / Rules Advisor
   ↓
Human Confirmation
   ↓
Spec / Contract
   ↓
Artifact Generation
   ↓
Deterministic Execution
   ↓
Data Quality / Reconciliation
   ↓
Evidence
```

## FAST
- one source/target;
- synthetic or controlled data;
- generated SQL/notebook;
- manual confirmation.

## MVP
- data contracts;
- schema checks;
- idempotent load strategy;
- DQ validation;
- execution evidence;
- lineage metadata.

## PRODUCT
- controlled promotion;
- rollback/reprocessing;
- schema evolution policy;
- lineage/catalog integration;
- quality SLOs;
- FinOps;
- permission-aware execution.

## Proven practice

Business Rules Silver demonstrated that successful compute execution alone is insufficient. The final acceptance must include post-execution reconciliation and business-level validation.

## Key rule

> Let the agent propose; let deterministic data engineering controls prove.
