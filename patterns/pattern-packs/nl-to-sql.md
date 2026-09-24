# Pack — NL-to-SQL

## Intent

Translate governed natural-language analytical questions into validated SQL and explain the result.

## Use when

- business users need conversational access to structured data;
- analytical questions can be expressed through a controlled data model;
- generated SQL can be constrained to approved datasets/views.

## Reference flow

```text
Question
  ↓
Intent + Semantic Context
  ↓
Schema / Metric Retrieval
  ↓
SQL Draft
  ↓
Static Validation
  ↓
Dry Run / Cost Check
  ↓
Execute
  ↓
Result Validation
  ↓
Narrative
```

## Required practices

- start from representative questions, expected SQL, and expected answers;
- enrich metadata and business definitions;
- begin with simple single-table queries;
- add joins progressively;
- validate SQL before execution;
- separate query generation from narrative generation;
- use a semantic layer where business metrics are non-trivial.

## FAST
- read-only sandbox dataset;
- limited schema;
- 10–20 benchmark questions.

## MVP
- schema/metadata retrieval;
- allowed tables/views;
- SQL parser/static checks;
- dry-run/cost limits;
- benchmark accuracy.

## PRODUCT
- permission-aware schema/data access;
- semantic layer;
- verified queries/examples;
- row/column policy enforcement;
- query budgets;
- audit trail;
- regression suite.

## Key rule

> NL-to-SQL quality depends as much on metadata and semantic modeling as on the LLM.
