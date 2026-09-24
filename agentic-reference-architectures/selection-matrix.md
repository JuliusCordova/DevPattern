# Agentic Architecture Selection Matrix

| Platform | FAST DEMO | MVP | PRODUCT |
|---|---|---|---|
| Azure | Prompt/Hosted Agent + model + simple tools | Foundry Agent Service + app runtime + tools/RAG + observability | Agent Framework/Hosted Agents + private networking + governed tools + HITL + operations |
| GCP | Cloud Run + ADK + Gemini + simple tools | Cloud Run + ADK + Vertex AI + tools/data + evals | Governed runtime + permission-aware tools + events + AgentOps + promotion gates |
| AWS | Bedrock + simple runtime/tools | AgentCore Runtime + Bedrock + governed tools + observability | AgentCore Runtime + Gateway + enterprise auth + private access + operations |
| Fabric | Fabric Data Agent + curated source | Data Agent + semantic model + instructions/evals | Governed Data Agent + semantic ownership + lineage + monitored runtime |

## Variant selection

```text
single-agent
  ↓ complexity grows
multi-agent

RAG
  ↓ relational/global gap proven
GraphRAG

request-driven
  ↓ async/long-running need
event-driven / long-running

data Q&A
  ↓ governed semantic analytics need
data-agent
```

## Escalation rule

Do not move from FAST DEMO to MVP or PRODUCT because of elapsed time.

Escalate because requirements or evidence justify it.
