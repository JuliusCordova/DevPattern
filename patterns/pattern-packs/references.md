# Authoritative References

The Pattern Pack catalog is informed by vendor documentation, open protocol specifications, and established engineering guidance. These sources are references, not mandatory implementations.

## Agent architecture

### OpenAI
- Practical Guide to Building Agents  
  https://openai.com/business/guides-and-resources/a-practical-guide-to-building-ai-agents/
- Agents documentation  
  https://developers.openai.com/learn/agents
- Agent evaluations  
  https://developers.openai.com/api/docs/guides/agent-evals
- Tracing  
  https://developers.openai.com/api/docs/guides/agents-api/tracing
- Code Interpreter  
  https://developers.openai.com/api/docs/guides/tools-code-interpreter

Key ideas adopted:
- start with a single agent where possible;
- introduce multi-agent orchestration only when complexity justifies it;
- establish eval baselines before optimizing model cost/latency;
- grade traces/tool choices, not only final responses;
- execute generated code in isolated sandboxes.

### Anthropic
- Building Effective Agents  
  https://www.anthropic.com/engineering/building-effective-agents
- Demystifying Evals for AI Agents  
  https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents

Key ideas adopted:
- prefer simple composable patterns;
- distinguish deterministic workflows from autonomous agents;
- evaluate trajectories/tool use as well as final outputs.

## Open interoperability protocols

### Model Context Protocol (MCP)
- MCP specification/blog — 2026-07-28  
  https://blog.modelcontextprotocol.io/posts/2026-07-28/
- MCP Tasks extension  
  https://tasks.extensions.modelcontextprotocol.io/specification/draft/tasks

Key ideas adopted:
- stateless protocol core for scalable MCP servers;
- schema-driven reusable tools/resources;
- authorization hardening;
- explicit long-running task lifecycle through the Tasks extension.

### Agent2Agent (A2A)
- A2A official site  
  https://a2a-protocol.org/
- Latest specification  
  https://a2a-protocol.org/latest/specification

Key ideas adopted:
- capability discovery via Agent Cards;
- interoperability across independently deployed agents;
- explicit task/artifact lifecycle;
- support for streaming and asynchronous collaboration.

## Google / GCP

### Agent Development Kit and Agents CLI
- ADK documentation  
  https://google.github.io/adk-docs/
- Agents CLI  
  https://google.github.io/agents-cli/
- Evaluation guide  
  https://google.github.io/agents-cli/guide/evaluation/
- Observability guide  
  https://google.github.io/agents-cli/guide/observability/
- Agent Runtime Code Execution  
  https://google.github.io/adk-docs/tools/google-cloud/code-exec-agent-engine/

Key ideas adopted:
- prototype-first workflow;
- structured eval datasets and trace grading;
- Cloud Trace/OpenTelemetry observability;
- sandboxed persistent code execution for agent tasks.

### Cloud Run agents and events
- Host AI agents on Cloud Run  
  https://cloud.google.com/run/docs/ai-agents
- Pub/Sub with Cloud Run  
  https://cloud.google.com/pubsub/docs/use-with-cloud-run
- Eventarc Pub/Sub triggers  
  https://cloud.google.com/run/docs/triggering/pubsub-triggers

Key ideas adopted:
- Services for request-driven agents;
- Jobs for run-to-completion work;
- Worker Pools for background agent fleets;
- Pub/Sub/Eventarc for event-driven activation.

### NL-to-SQL / BigQuery
- NL2SQL with BigQuery and Gemini  
  https://cloud.google.com/blog/products/data-analytics/nl2sql-with-bigquery-and-gemini
- Gemini in BigQuery  
  https://cloud.google.com/bigquery/docs/gemini-overview

Key ideas adopted:
- begin from representative questions, expected SQL and expected answers;
- enrich metadata/business definitions;
- progress from simple queries to complex joins;
- use verified queries and semantic context.

### Semantic data
- BigQuery overview / AI-ready data platform  
  https://cloud.google.com/bigquery/docs/introduction
- dbt Semantic Layer  
  https://docs.getdbt.com/

Key ideas adopted:
- centralize metrics and business definitions;
- expose entities, dimensions, measures and join semantics consistently to AI and analytics consumers.

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
