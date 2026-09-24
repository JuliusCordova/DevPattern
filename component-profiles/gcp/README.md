# GCP Component Architecture Profile

## Status

```yaml
platform: gcp
review_cadence: weekly
baseline_evidence: PROVEN
```

The GCP profile should build on the proven practices already captured in:

- `patterns/implementation-profiles/gcp/`
- `JuliusCordova/portafoliodatagob`
- `JuliusCordova/bussinesrulessilver`
- `JuliusCordova/pricingprima`

## Workload profiles

Planned component mappings:

- web-app;
- agentic-app;
- rag;
- event-driven;
- data-platform.

## Current baseline principle

For request-driven agentic products:

```text
Cloud Run
   ↓
ADK / Agent Runtime
   ↓
Vertex AI / Gemini
   ↓
Deterministic domain services
   ↓
BigQuery / Cloud SQL / APIs
```

This is a baseline, not a permanent mandate.

New GCP capabilities are reviewed weekly and replace this baseline only when there is evidence of material architectural improvement.
