# GCP Workload Component Mappings

Status: CURRENT  
Evidence: PROVEN + OFFICIAL  
Review cadence: weekly

Reference projects:
- portafoliodatagob
- bussinesrulessilver
- pricingprima

## 1. Web App

### FAST DEMO
- Cloud Run
- Cloud SQL or BigQuery only if persistence is required

### MVP
- Cloud Run
- Cloud SQL / BigQuery depending workload
- Secret Manager
- dedicated service account
- Cloud Logging / Monitoring
- Artifact Registry

### PRODUCT
Add only when required:
- private ingress / load balancing
- VPC connectivity
- Cloud Armor
- HA database configuration
- controlled CI/CD and promotion gates

## 2. Agentic App

### FAST DEMO
- Cloud Run
- Google ADK
- Vertex AI / Gemini
- local or simple tools

### MVP
- Cloud Run
- ADK
- Vertex AI
- explicit tool contracts
- BigQuery / Cloud SQL / APIs
- Secret Manager
- Logging / Monitoring
- eval dataset
- Artifact Registry + Cloud Build

### PRODUCT
Add when justified:
- private connectivity
- permission-aware tools
- AgentOps / FinOps telemetry
- promotion evidence
- rollback
- Worker Pools for background fleets
- Cloud Run Jobs for batch/evals

Official reference:
https://docs.cloud.google.com/run/docs/ai-agents

## 3. RAG App

### FAST DEMO
- Cloud Run
- ADK or simple application runtime
- Vertex AI model
- Cloud Storage source
- simple vector/retrieval implementation

### MVP
- metadata-aware ingestion
- managed vector/search capability
- Cloud Storage / BigQuery source
- hybrid retrieval where justified
- groundedness/citation evals

### PRODUCT
Add:
- permission-aware retrieval
- incremental ingestion
- reranking only when measured
- lineage/freshness
- retrieval observability
- regression benchmark

## 4. Event-Driven

### FAST DEMO
- Pub/Sub
- Cloud Run

### MVP
- Pub/Sub
- Eventarc
- Cloud Run
- event schema
- retry / dead-letter behavior
- idempotency

### PRODUCT
Add when required:
- ordered delivery strategy
- DLQ operations
- replay
- cross-project IAM boundaries
- tracing / SLOs

Official reference:
https://docs.cloud.google.com/eventarc/standard/docs/run/bigquery

## 5. Data Platform

### FAST DEMO
- Cloud Storage
- BigQuery
- simple SQL / notebook transformations

### MVP
- Cloud Storage
- BigQuery
- Dataform / Dataproc / managed processing only when justified
- data contracts
- DQ validation
- lineage/governance

### PRODUCT
Add according to need:
- Dataplex governance
- event-driven ingestion
- workload isolation
- FinOps
- DR/resilience
- private connectivity

## Default principle

> Cloud Run remains the default application/agent runtime until a concrete workload requirement proves another runtime is necessary.
