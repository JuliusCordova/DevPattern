# AWS Agentic Reference Architecture

Status: CURRENT  
Evidence: OFFICIAL  
Review cadence: weekly

## FAST DEMO

```mermaid
flowchart LR
    U[User] --> APP[Simple App / Lambda / Fargate]
    APP --> BR[Amazon Bedrock Model]
    APP --> T[Direct Tools]
    T --> D[(Optional S3 / DynamoDB)]
```

Use AgentCore Runtime only when the demo actually needs a managed agent runtime.

Avoid by default:
- EKS
- private multi-account topology
- complex gateways
- dedicated clusters

## MVP

```mermaid
flowchart TB
    UI[Web / API] --> APIG[API Gateway]
    APIG --> APP[Lambda / ECS Fargate]
    APP --> ACR[AgentCore Runtime]
    ACR --> BR[Amazon Bedrock Models]
    ACR --> T[Governed Tools]
    ACR --> KB[Knowledge Bases]
    T --> S3[(S3)]
    T --> DDB[(DynamoDB)]
    T --> AU[(Aurora)]
    ACR --> IAM[IAM Roles]
    ACR --> SM[Secrets Manager]
    ACR --> CW[CloudWatch]
```

Recommended baseline:
- AgentCore Runtime where managed agent execution is required
- Bedrock
- explicit IAM roles
- Secrets Manager
- CloudWatch
- governed tool contracts
- Knowledge Bases when RAG is required

## PRODUCT

```mermaid
flowchart TB
    CH[Channels] --> EDGE[CloudFront / WAF / API Gateway]
    EDGE --> APP[Agent Application]
    APP --> ACR[AgentCore Runtime]
    ACR --> GW[AgentCore Gateway]
    GW --> MCP[MCP Tools]
    GW --> HTTP[HTTP APIs]
    GW --> AG[Agent Targets]
    MCP --> SYS[Enterprise Systems]
    HTTP --> SYS
    AG --> SYS
    ACR --> IAM[IAM / OAuth]
    ACR --> NET[Private Access / VPC Endpoints]
    ACR --> OBS[CloudWatch / Audit / AgentOps]
    ACR --> HITL[Human Approval]
```

Add only when justified:
- AgentCore Gateway
- centralized inbound/outbound authorization
- private networking / VPC endpoints
- cross-account controls
- multi-agent
- HITL
- release gates
- persistent/durable state

## Variants

### Single Agent
Bedrock + AgentCore Runtime where needed.

### RAG Agent
Add Bedrock Knowledge Bases or selected vector store.

### Multi-Agent
Use only when independent agents or security/ownership boundaries justify it.

### MCP / Enterprise Tool Access
Use AgentCore Gateway when centralized tool discovery, MCP access and authorization materially improve governance.

## Current platform note

AgentCore Gateway provides a unified connectivity layer between agents and tools/resources and supports MCP-based access to configured targets.
