# Authoritative References

The Pattern Pack catalog is informed by vendor documentation and established engineering guidance. These sources are references, not mandatory implementations.

## Agent architecture

### OpenAI
- Practical Guide to Building Agents  
  https://openai.com/business/guides-and-resources/a-practical-guide-to-building-ai-agents/
- Agents SDK documentation  
  https://openai.github.io/openai-agents-python/

Key ideas adopted:
- start with a single agent where possible;
- introduce multi-agent orchestration when complexity justifies it;
- define tools clearly;
- use guardrails and human intervention for higher-risk actions.

### Anthropic
- Building Effective Agents  
  https://www.anthropic.com/engineering/building-effective-agents
- Demystifying Evals for AI Agents  
  https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents

Key ideas adopted:
- prefer simple composable patterns;
- distinguish deterministic workflows from autonomous agents;
- evaluate trajectories/tool use as well as final outputs.

## Google / GCP

### Agent Development Kit
- ADK documentation  
  https://google.github.io/adk-docs/
- Evaluation  
  https://google.github.io/adk-docs/evaluate/

### Cloud Run agents
- Host AI agents on Cloud Run  
  https://cloud.google.com/run/docs/ai-agents
- Build and deploy ADK agent on Cloud Run  
  https://cloud.google.com/run/docs/ai/build-and-deploy-ai-agents/deploy-adk-agent

Key ideas adopted:
- ADK as a modular code-first agent framework;
- Cloud Run Service for stateless request-driven agents;
- Cloud Run Jobs for run-to-completion work;
- Worker Pools for background distributed workloads.

## RAG

### Microsoft Azure AI Search
- RAG overview and retrieval guidance  
  https://learn.microsoft.com/azure/search/retrieval-augmented-generation-overview

Key ideas adopted:
- hybrid lexical + vector retrieval where appropriate;
- metadata filtering;
- reranking based on measured benefit;
- retrieval quality as an evaluated subsystem.

## GraphRAG

### Microsoft Research / GraphRAG
- GraphRAG repository  
  https://github.com/microsoft/graphrag
- GraphRAG documentation  
  https://microsoft.github.io/graphrag/

Key ideas adopted:
- entity and relationship extraction;
- community detection and summaries;
- local vs global query strategies;
- GraphRAG should solve a measured relational/global retrieval problem rather than replace RAG by default.

## GCP implementation evidence

The GCP profile also uses implementation evidence from:
- https://github.com/JuliusCordova/portafoliodatagob
- https://github.com/JuliusCordova/bussinesrulessilver
- https://github.com/JuliusCordova/pricingprima

The reusable lessons extracted from these projects are documented under:
- `patterns/implementation-profiles/gcp/`
