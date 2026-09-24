# Azure Workload Component Mappings

Status: CURRENT  
Evidence: OFFICIAL  
Review cadence: weekly

## 1. Web App

### FAST DEMO
- Azure App Service or Azure Container Apps
- Azure SQL / PostgreSQL only if persistence is required

### MVP
- App Service or Container Apps
- Azure SQL / Azure Database for PostgreSQL
- Managed Identity
- Key Vault
- Application Insights / Azure Monitor
- Container Registry when containerized

### PRODUCT
Add when required:
- Front Door / Application Gateway
- WAF
- private endpoints
- zone/resilience design
- API Management
- deployment slots / controlled promotion

## 2. Agentic App

### FAST DEMO
- App Service / Container Apps
- Microsoft Foundry
- Foundry Agent Service
- model deployment

### MVP
- App Service / Container Apps
- Foundry project/resource
- Foundry Agent Service
- managed identity
- Key Vault
- Application Insights / Azure Monitor
- explicit tool contracts

### PRODUCT
Add only when justified:
- AI Search
- managed Redis
- Cosmos DB / Azure SQL / PostgreSQL
- private endpoints
- API Management
- network isolation
- policy/guardrails
- multi-agent runtime separation

Official references:
https://learn.microsoft.com/en-us/azure/foundry/concepts/architecture
https://learn.microsoft.com/en-us/azure/architecture/solution-ideas/articles/ai-agents-at-scale

## 3. RAG App

### FAST DEMO
- App Service / Container Apps
- Foundry Agent Service
- Foundry IQ knowledge base or Azure AI Search
- Blob Storage / enterprise source

### MVP
- managed ingestion
- Foundry IQ / AI Search
- metadata filters
- citations
- Managed Identity
- evals

### PRODUCT
Add:
- permission-aware retrieval
- private endpoints
- hybrid/vector retrieval tuning
- freshness/lineage
- retrieval telemetry
- regression benchmark

Official reference:
https://learn.microsoft.com/en-us/azure/app-service/tutorial-ai-openai-search-java

## 4. Event-Driven

### FAST DEMO
- Azure Functions or Container Apps
- Event Grid

### MVP
- Event Grid and/or Service Bus based on semantics
- Functions / Container Apps
- retry handling
- dead-letter handling
- idempotency

### PRODUCT
Add:
- private endpoints
- topic/queue isolation
- replay strategy
- observability
- resilient consumer design

## 5. Data Platform

### FAST DEMO
- Blob Storage / ADLS
- Azure SQL or basic analytical store where sufficient

### MVP
- ADLS
- Data Factory
- Databricks or Fabric depending analytical strategy
- Purview when governance is required

### PRODUCT
Add:
- private networking
- enterprise governance
- catalog/lineage
- workload isolation
- DR
- cost governance

## Default principle

> Prefer managed PaaS first. Introduce AKS or more complex network/runtime architecture only when scale, isolation, or operational requirements justify it.
