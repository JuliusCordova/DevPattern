# Pack — Semantic Layer

## Intent

Provide governed business meaning between raw data structures and AI/agent experiences.

## Use when

- users ask for business metrics, not columns;
- the same metric must mean the same thing across BI, NL-to-SQL, agents, and APIs;
- joins and calculation logic should not be reinvented by the LLM.

## Semantic assets

- entities;
- dimensions;
- measures;
- metrics;
- business glossary;
- synonyms;
- approved join paths;
- time semantics;
- verified queries/examples.

## Structure

```text
Raw / Curated Data
      ↓
Semantic Models
      ↓
Metrics + Entities + Business Definitions
      ↓
NL-to-SQL / BI / Agents
```

## FAST
- glossary + curated views may be enough.

## MVP
- central metric definitions;
- entity/join metadata;
- synonyms;
- verified queries.

## PRODUCT
- governed metric lifecycle;
- versioning;
- ownership;
- access policies;
- lineage;
- semantic regression tests.

## Key rule

> Agents should reason over business meaning, not guess business meaning from physical schemas.
