# Component Architecture Profiles

Component Architecture Profiles translate vendor-neutral DevPattern architecture and Pattern Packs into concrete cloud services.

They answer:

> Which managed components should implement the selected architecture on this platform **today**?

They do **not** replace architecture patterns.

## Separation of concerns

```text
Definition Pack
     ↓
Architecture Pattern
     ↓
Pattern Packs
     ↓
Component Architecture Profile
     ↓
Implementation
```

Examples:

- Hexagonal Slice remains an architecture pattern.
- RAG remains a Pattern Pack.
- Azure AI Search, Vertex AI Search, OpenSearch, BigQuery, Cloud Run, Container Apps, Bedrock, OneLake, and similar services belong to Component Architecture Profiles.

## Initial platforms

```text
component-profiles/
├── azure/
├── fabric/
├── gcp/
└── aws/
```

Each platform should organize recommendations by workload rather than by individual cloud service.

Preferred workload profiles:

- web application;
- agentic application;
- RAG / knowledge application;
- event-driven application;
- data platform;
- semantic / analytics application where applicable.

## Progressive selection

Component profiles follow the same maturity progression:

```text
FAST DEMO
    ↓
Minimum deployable component set

MVP
    ↓
Repeatable, observable and testable component set

PRODUCT
    ↓
Secure, resilient, governed and scalable component set
```

The goal is **not** to add more services at every stage.

A new managed service or boundary is introduced only when it materially improves:

- simplicity;
- delivery speed;
- security;
- scalability;
- resilience;
- operability;
- integration;
- cost;
- maintainability.

## Core rule

> Patterns define how the system behaves. Component Profiles define how the selected pattern is realized on a platform.

## Freshness requirement

Cloud services evolve continuously.

Component Architecture Profiles are therefore **living artifacts** and must be reviewed weekly.

See [Weekly Review Policy](weekly-review-policy.md).
