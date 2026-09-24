# Pattern Selection — Cross-Industry Legal Contract Intelligence FAST DEMO

## Fixed implementation decisions

- Product: cross-industry demo, not client-specific.
- Frontend: React.
- Backend/API: FastAPI.
- Cloud: GCP.
- Agent runtime: Google ADK + Vertex AI/Gemini.

## Selected patterns

### 1. PA-SDD / FAST DEMO
Use a Minimum Sufficient Specification and a simple feature slice.

Why:
- value is not yet validated;
- documentation and controls remain proportional to maturity;
- acceptance evidence matters more than architecture volume.

### 2. React -> FastAPI boundary
React owns presentation and interaction state.
FastAPI owns server-side API contracts, agent invocation and access to retrieval/model services.

Rules:
- no model credentials in React;
- no direct browser-to-Gemini calls;
- API schemas remain explicit and testable;
- client-specific behavior is not hardcoded into either layer.

### 3. Single Agent
One visible Legal Contract Intelligence Agent.

Why:
- the demo requires one coherent user task;
- search, clause analysis and comparison can remain capabilities/tools;
- multi-agent orchestration adds latency, cost and failure modes without proving more business value.

Evolution trigger:
- specialist reasoning becomes materially different;
- tool/action permissions diverge;
- independent scaling or evaluation is required;
- orchestration complexity is justified by evidence.

### 4. RAG
Retrieve contract evidence before answer generation.

Why:
- legal answers must be grounded in the supplied corpus;
- evidence must remain inspectable;
- abstention is possible when retrieval returns insufficient support.

### 5. Tool Calling
Use only two agent tools:
- `search_contracts`
- `get_document`

Why:
- separates model reasoning from deterministic retrieval;
- keeps the agent contract small and testable.

### 6. Context Engineering
Assemble model context from:
- system/agent contract;
- current user question;
- retrieved evidence;
- minimal conversation context;
- explicit response constraints.

Do not place the full corpus into the prompt.

### 7. Cross-industry core + adapters/configuration
Core behavior is reusable.
Client specialization is a future configuration/integration concern.

This avoids client forks and keeps the FAST DEMO portable.

### 8. Governed Agent — minimal FAST DEMO subset
Apply only controls that materially affect the demo:
- read-only runtime;
- bounded tools;
- source-grounded answers;
- safe abstention;
- no hidden external knowledge source;
- no autonomous legal decision.

### 9. Eval + Observability — minimal subset
Collect:
- golden-set pass/fail;
- grounding/evidence correctness;
- unsupported-answer rate;
- latency;
- errors;
- smoke-test result.

Do not introduce the full AgentOps control/observability plane in FAST DEMO.

## Explicitly not selected

- Multi-Agent Manager
- A2A
- MCP
- GraphRAG
- Long-running agent
- Event-driven agent
- Human approval workflow
- complex memory
- code execution
- client-specific enterprise integration

These may be introduced only after a concrete requirement or measured limitation appears.

## Reuse from portafoliodatagob

Reusable engineering knowledge, not mandatory copied code:

1. **ADK runtime structure**
   - Google ADK Agent on Gemini.
   - Explicit instructions and bounded tools.

2. **RAG-lite design**
   - Stable retrieval service returning ranked chunks, scores and excerpts.
   - Query composition separated from retrieval implementation.

3. **Governance principle**
   - do not invent missing facts;
   - deterministic tools provide governed outputs;
   - agents recommend/explain while humans decide.

4. **Demo readiness**
   - synthetic/curated demo data is versioned, not hardcoded;
   - demo state is repeatable;
   - demo behavior is independently testable.

5. **Smoke testing**
   - non-destructive by default;
   - health endpoint;
   - web reachability;
   - React/FastAPI integration verification;
   - mutation checks opt-in only.

6. **AgentOps principle for later maturity**
   - stable IDs for systems/agents/runs;
   - separate control-plane concerns from high-volume observability;
   - never invent unavailable metrics;
   - do not persist prompts/responses by default.

## Key decision

> Reuse proven engineering knowledge from ATLAS DataGob while keeping the cross-industry Legal FAST DEMO intentionally smaller than production-oriented patterns.
