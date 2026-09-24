# GCP Agentic Reference Architecture

Status: CURRENT  
Evidence: PROVEN + OFFICIAL  
Review cadence: weekly

Proven by DevPattern reference implementations including DataGob, Business Rules Silver, and PricingPrima.

## FAST DEMO

```mermaid
flowchart LR
    U[User] --> CR[Cloud Run Service]
    CR --> ADK[Google ADK]
    ADK --> V[Vertex AI / Gemini]
    ADK --> T[1-3 Simple Tools]
    T --> D[(Optional BigQuery / Cloud SQL)]
```

Recommended baseline:
- Cloud Run Service
- Google ADK
- Vertex AI / Gemini
- simple tools
- optional BigQuery / Cloud SQL
- scale-to-zero where appropriate

Avoid by default:
- GKE
- service mesh
- dedicated clusters
- unnecessary private networking
- multi-agent

## MVP

```mermaid
flowchart TB
    UI[Frontend] --> CR[Cloud Run API / Agent Runtime]
    CR --> ADK[ADK Agent]
    ADK --> V[Vertex AI]
    ADK --> T[Tool Contracts]
    T --> BQ[(BigQuery)]
    T --> SQL[(Cloud SQL)]
    T --> API[Enterprise APIs]
    CR --> SA[Dedicated Service Account]
    CR --> SM[Secret Manager]
    CR --> OBS[Cloud Logging / Monitoring]
    CI[Cloud Build] --> AR[Artifact Registry]
    AR --> CR
    OBS --> EVAL[Evals + Outcome Evidence]
```

Recommended baseline:
- Cloud Run
- ADK
- Vertex AI
- dedicated service account
- Secret Manager
- Cloud Logging / Monitoring
- Artifact Registry
- Cloud Build
- explicit tool contracts
- eval dataset
- outcome evidence

## PRODUCT

```mermaid
flowchart TB
    CH[Channels] --> IN[Controlled Ingress]
    IN --> CR[Cloud Run Agent Runtime]
    CR --> ADK[ADK Orchestrator]
    ADK --> GOV[Permission-Aware Tools / Agents]
    GOV --> BQ[(BigQuery)]
    GOV --> SQL[(Cloud SQL)]
    GOV --> API[Enterprise APIs]
    EVT[Pub/Sub / Eventarc] --> CR
    JOB[Cloud Run Jobs] --> ADK
    WP[Worker Pools when justified] --> ADK
    CR --> OBS[AgentOps / FinOps / Trace]
    OBS --> EVID[Evidence Pack]
    EVID --> GATE[Promotion Gate]
```

Add only when justified:
- private ingress
- VPC connectivity
- PSC
- Cloud NAT
- Pub/Sub/Eventarc
- Worker Pools
- Cloud Run Jobs
- multi-agent
- durable approval state
- release promotion/rollback

## Cloud Run resource rule

- Service: request-driven agent
- Job: run-to-completion / batch / eval
- Worker Pool: background agent fleet
- Instance: dedicated stateful singleton loop

## Key rule

> Cloud Run remains the default until a concrete workload limitation proves the need for another runtime.
