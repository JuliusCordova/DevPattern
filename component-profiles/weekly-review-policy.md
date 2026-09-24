# Weekly Review Policy for Cloud Component Profiles

## Purpose

Cloud component recommendations must remain current without turning DevPattern into a technology-chasing exercise.

The review cadence is:

> **Weekly review, evidence-based change.**

## What must be reviewed

For Azure, Microsoft Fabric, GCP, and AWS, review material changes in:

- agent runtimes and agent frameworks;
- model platforms;
- RAG and vector search;
- semantic layer capabilities;
- databases and analytical stores;
- serverless and container runtimes;
- eventing and messaging;
- workflow/orchestration;
- identity and authorization;
- secrets and key management;
- observability and tracing;
- security controls;
- networking/private access;
- deployment and CI/CD;
- quotas and relevant service limits;
- pricing changes that materially affect architecture;
- deprecations, replacements and service renames;
- official reference architectures.

## Source priority

Use sources in this order:

1. Official cloud documentation.
2. Official architecture/reference guides.
3. Official release notes or product announcements.
4. Proven DevPattern project implementations.
5. Experimental validation.

Community content may provide discovery signals but should not establish a baseline recommendation by itself.

## Recommendation lifecycle

```text
New capability detected
        ↓
Official source verification
        ↓
Compare to current recommendation
        ↓
Does it materially improve the architecture?
        │
   NO ──┴── YES
   │          │
Document      Validate
only          impact
              ↓
         Update profile
```

## Important rule

> A weekly refresh does not automatically change the recommended architecture.

A recommendation changes only when the new option materially improves one or more of:

- simplicity;
- security;
- cost;
- delivery speed;
- scalability;
- resilience;
- observability;
- developer experience;
- interoperability;
- operational control.

## Profile status

Every profile must have one lifecycle status:

- **CURRENT** — valid current recommendation.
- **REVIEW_REQUIRED** — material change detected; evaluation pending.
- **DEPRECATED** — should no longer be selected for new implementations.
- **REPLACED** — superseded by another recommendation.

## Evidence level

Each recommendation also declares an evidence level:

- **OFFICIAL** — supported by current official platform documentation.
- **PROVEN** — official and additionally exercised successfully in a DevPattern reference implementation.
- **EXPERIMENTAL** — technically promising but not yet a baseline recommendation.

These are independent dimensions.

Example:

```yaml
component:
  name: cloud_run
  lifecycle_status: CURRENT
  evidence_level: PROVEN
```

## Weekly review output

Each weekly review should produce:

- review date;
- sources checked;
- material changes detected;
- affected profiles;
- decision: no change / review required / update / deprecate / replace;
- rationale;
- changelog entry when a recommendation changes.

No-change reviews are valid evidence and should not generate unnecessary architectural churn.
