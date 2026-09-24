# Pattern Selection — Legal Contract Agent FAST DEMO

## Selected patterns

### 1. PA-SDD / FAST DEMO
Use a Minimum Sufficient Specification and a simple feature slice.

Why:
- value is not yet validated;
- documentation and controls must remain proportional to maturity;
- acceptance evidence is more important than architecture volume.

### 2. Single Agent
One visible Legal Contract Agent.

Why:
- the demo requires one coherent user task;
- search, clause analysis and comparison can remain capabilities/tools;
- multi-agent orchestration would add latency, cost and failure modes without proving more business value.

Evolution trigger:
- specialist reasoning becomes materially different;
- tool/action permissions diverge;
- independent scaling or evaluation is required;
- orchestration complexity can be demonstrated with evidence.

### 3. RAG
Retrieve contract evidence before answer generation.

Why:
- legal answers must be grounded in the supplied corpus;
- evidence needs to remain inspectable by the user;
- abstention is possible when retrieval returns insufficient support.

### 4. Tool Calling
Use only two tools:
- `search_contracts`
- `get_document`

Why:
- separates model reasoning from deterministic retrieval;
- keeps the agent contract small and testable.

### 5. Context Engineering
The model context must be assembled from:
- system/agent contract;
- current user question;
- retrieved evidence;
- minimal conversation context;
- explicit response constraints.

Do not place the full corpus into the prompt.

### 6. Governed Agent — minimal FAST DEMO subset
Apply only the controls that materially affect the demo:
- read-only runtime;
- bounded tools;
- source-grounded answers;
- safe abstention;
- no hidden external knowledge source;
- no autonomous legal decision.

### 7. Eval + Observability — minimal subset
Collect only evidence needed to trust the demo:
- golden-set pass/fail;
- grounding/evidence correctness;
- unsupported-answer rate;
- latency;
- errors;
- smoke-test result.

Do not introduce the full reusable AgentOps control/observability plane in FAST DEMO.

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

These may be introduced only after a concrete requirement or measured limitation appears.

## Reuse from portafoliodatagob

The following implementation knowledge is reusable as engineering evidence, not as mandatory copied code:

1. **ADK runtime structure**
   - Google ADK Agent on Gemini.
   - Explicit instructions and bounded tools.
   - Agent-visible vs specialist/tool separation.

2. **RAG-lite design**
   - Stable retrieval service returning ranked chunks, scores and excerpts.
   - Query composition separated from retrieval implementation.

3. **Governance principle**
   - do not invent missing facts;
   - deterministic tools provide governed outputs;
   - agents recommend/explain while humans decide.

4. **Demo readiness**
   - synthetic/curated demo data should be versioned, not hardcoded into application logic;
   - demo state should be repeatable;
   - demo behavior should be independently testable.

5. **Smoke testing**
   - non-destructive smoke by default;
   - health endpoint;
   - web reachability;
   - API/web integration verification;
   - mutation checks opt-in only.

6. **AgentOps principle for later maturity**
   - stable IDs for systems/agents/runs;
   - separate control-plane concerns from high-volume observability;
   - never invent unavailable metrics;
   - do not persist prompts/responses by default.

## Key decision

> Reuse the proven engineering knowledge from ATLAS DataGob, but keep the Legal FAST DEMO simpler than ATLAS production-oriented patterns.
