# Pattern Pack → GCP Mapping

This mapping provides a default implementation path, not a mandatory architecture.

| PA-SDD Pattern Pack | GCP default | Escalate only when |
|---|---|---|
| AI Workflow | Cloud Run + deterministic orchestration | long-running/durable state requires workflow engine |
| Single Agent | ADK + Cloud Run + Vertex AI | persistent managed agent runtime adds clear value |
| Tool Calling | Python/ADK tools + service adapters | shared enterprise tools justify MCP or separate service |
| RAG | Vertex AI / BigQuery / managed vector capability depending corpus | measured retrieval requirements demand specialization |
| GraphRAG | Graph extraction + graph store/query layer + LLM synthesis | baseline RAG fails relational/global benchmark |
| Multi-Agent Manager | ADK orchestrator + specialist agents | context/security/specialization justify split |
| Handoff | ADK transfer/routing + bounded context | ownership truly needs to move |
| HITL | API workflow + persistent approval state | complex long-running workflow needs dedicated orchestration |
| Memory | ADK session state / application persistence | durable cross-session memory is justified |
| Governed Agent | IAM + service accounts + filters + audit | always increase controls with data/action risk |

## Single Agent — recommended GCP shape

```text
Cloud Run
  ↓
ADK Agent
  ↓
Gemini on Vertex AI
  ↓
Tools
  ├─ BigQuery
  ├─ internal API
  └─ deterministic domain services
```

## RAG — recommended GCP shape

```text
Source content
   ↓
Ingestion / normalization
   ↓
Chunk + metadata
   ↓
Vector + keyword index
   ↓
Permission / metadata filter
   ↓
Retriever
   ↓
Rerank if justified
   ↓
ADK Agent
   ↓
Cited response
```

For PRODUCT, retrieval must preserve identity/authorization boundaries and source provenance.

## GraphRAG — recommended GCP shape

Do not prescribe a graph technology before the benchmark.

```text
Documents / enterprise entities
    ↓
Entity + relationship extraction
    ↓
Graph representation
    ↓
Community / relationship analysis
    ↓
Local or global retrieval
    ↓
ADK orchestration
    ↓
Grounded synthesis
```

Promotion requirement:

```text
GraphRAG quality
      >
Baseline RAG quality
by a predefined meaningful margin
```

Otherwise keep baseline RAG.

## Multi-Agent — recommended GCP shape

```text
Cloud Run API
    ↓
ADK Manager
    ├─ Specialist A
    ├─ Specialist B
    └─ Specialist C
    ↓
Deterministic domain services
```

Do not deploy each specialist as a separate Cloud Run service automatically.

Start in-process. Split deployment only for:
- security boundary;
- independent scaling;
- independent release lifecycle;
- separate team ownership;
- dependency/runtime isolation.

## Cloud Run resource selection

```text
Interactive/request-driven
        → Service

Scheduled/batch/evaluation
        → Job

Background queue consumer/fleet
        → Worker Pool

Dedicated always-on singleton loop
        → Instance
```

## Secrets and identity

PRODUCT defaults:
- Secret Manager for secrets;
- dedicated runtime service account;
- no embedded credentials;
- minimum IAM permissions;
- separate identities where capabilities have different risk profiles.

## Deployment pattern

```text
Git
 ↓
Tests + Evals
 ↓
Cloud Build
 ↓
Artifact Registry
 ↓
Candidate Cloud Run Revision/Service
 ↓
Smoke + Outcome Validation
 ↓
Evidence
 ↓
Promotion Gate
 ↓
Production
```
