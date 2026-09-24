# GCP Implementation Profile

This profile maps PA-SDD Pattern Packs to a **GCP implementation that has already been exercised in the DevPattern reference projects**.

Reference projects:

- `JuliusCordova/portafoliodatagob`
- `JuliusCordova/bussinesrulessilver`
- `JuliusCordova/pricingprima`

The goal is not to force every GCP product into the same stack. It is to reuse the decisions that have worked and keep only the minimum architecture required by the product.

## Proven default

For request-driven agentic applications:

```text
User / UI
   ↓
Cloud Run Frontend
   ↓
Cloud Run API / Agent Runtime
   ↓
ADK Agent / Orchestrator
   ↓
Deterministic Tools / Domain Services
   ├─ BigQuery
   ├─ Vertex AI
   ├─ APIs
   ├─ Dataproc / Jobs when required
   └─ External systems
```

## Preferred GCP components

| Concern | Preferred default |
|---|---|
| Agent framework | Google ADK when GCP-native |
| Model runtime | Vertex AI / Gemini |
| HTTP agent runtime | Cloud Run Service |
| Background agent fleet | Cloud Run Worker Pool / Pub/Sub where justified |
| Batch / eval / scheduled run | Cloud Run Job |
| Container registry | Artifact Registry |
| CI/CD | Cloud Build or GitHub Actions → Cloud Build |
| Analytical data | BigQuery |
| Secrets | Secret Manager |
| Identity | Dedicated service account per runtime |
| Infrastructure | Terraform for MVP/Product |
| Logs/metrics | Cloud Logging / Monitoring |
| Agent evidence | Application traces + persisted run/eval evidence |
| Human approval | Application workflow with durable approval state |

Google Cloud supports ADK agents directly on Cloud Run and recommends choosing Cloud Run Services for stateless request-driven agents, Jobs for run-to-completion workloads, and Worker Pools for background queue-consuming fleets.

## Principle learned from reference implementations

> The LLM interprets, orchestrates and explains; deterministic services calculate and enforce critical rules.

This is explicit in PricingPrima and is also consistent with the Business Rules Silver implementation.

## Progressive use

### FAST

```text
ADK / simple Python agent
        ↓
Cloud Run
        ↓
Vertex AI / Gemini
        ↓
1–3 tools
```

Allow:
- source deployment;
- synthetic data;
- minimal infrastructure;
- basic smoke test.

Do not require:
- full Terraform;
- multi-agent;
- complex networking;
- separate microservices unless needed.

### MVP

Add:
- container image in Artifact Registry;
- dedicated service account;
- BigQuery/data contracts;
- Cloud Build pipeline;
- integration + agent smoke tests;
- evidence collection;
- explicit tool contracts;
- Terraform for stable infrastructure.

### PRODUCT

Add when justified:
- private ingress / controlled exposure;
- least-privilege IAM;
- Secret Manager;
- production observability;
- eval regression;
- release candidate promotion gate;
- rollback/versioned image;
- permission-aware retrieval/tools;
- FinOps telemetry;
- SLO/runbooks.

## Anti-overengineering rule

Do not introduce GKE, complex service mesh, multi-agent topology, graph stores, or event infrastructure unless workload behavior requires them.

Cloud Run remains the default until a concrete limitation is demonstrated.
