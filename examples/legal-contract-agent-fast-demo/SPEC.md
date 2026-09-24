# FAST DEMO SPEC — Cross-Industry Legal Contract Intelligence on GCP

Status: Ready for FAST DEMO implementation  
Maturity: FAST DEMO  
Cloud: Google Cloud  
Backend: FastAPI  
Frontend: React  
Pattern baseline: PA-SDD + GCP FAST DEMO

## 1. Business Intent

### Problem
Legal and contract-management users across industries spend significant time reviewing agreements manually to answer focused questions about clauses, obligations, penalties, validity, confidentiality and differences across documents.

### Desired Outcome
Demonstrate a reusable cross-industry legal intelligence experience where a user can ask natural-language questions over a controlled contract corpus and receive grounded, traceable answers supported by source evidence.

### Product Boundary
This is a cross-industry demonstration product. It must not embed client-specific names, workflows, policies, SharePoint structures or proprietary business rules in the core.

Future client implementations should extend the core through configuration, integrations and governed policies rather than forking core legal behavior.

### Success Metric
For a curated demo set:
- answer correctness >= 80%
- evidence correctness >= 90%
- unsupported answer rate <= 10%

## 2. Scope

### In Scope
- Cross-industry curated/synthetic corpus of digital PDF/DOCX contracts.
- Representative contract types such as services, supplier, NDA/confidentiality, technology, lease and consulting agreements.
- Text extraction and contract-aware chunking.
- Querying contracts in natural language.
- Clause analysis.
- Comparison of at least two contracts.
- Source evidence in each grounded answer.
- Explicit abstention when evidence is insufficient.
- React web experience.
- FastAPI backend/API.
- Functional deployment on GCP.
- Basic smoke validation.

### Out of Scope
- Any client-specific integration or branding.
- SharePoint integration.
- OCR/scanned-document pipeline.
- GraphRAG / knowledge graph.
- Multi-agent topology.
- MCP/A2A.
- Automated legal decisions or approvals.
- Contract generation/modification.
- Enterprise IAM/ABAC inherited from source systems.
- VPC/PSC/private networking.
- HA/DR/SLO production controls.
- Full AgentOps / FinOps.
- Full Terraform/enterprise CI/CD.

## 3. Actor / Persona

### Legal / Contract Specialist
Needs to locate, understand and compare contract content without knowing prompt syntax, cloud services or retrieval mechanics.

## 4. User Stories

### US-001 — Query contracts
As a legal specialist  
I want to ask natural-language questions over the available contracts  
So that I can locate relevant contractual information quickly.

### US-002 — Analyze clauses
As a legal specialist  
I want the agent to identify and explain a relevant clause  
So that I can understand the contractual condition with source evidence.

### US-003 — Compare contracts
As a legal specialist  
I want to compare the same type of clause in two contracts  
So that I can identify material differences.

### US-004 — Verify evidence
As a legal specialist  
I want to see the source document and supporting excerpt  
So that I can verify the answer myself.

## 5. Functional Requirements

- FR-FD-01: The system shall load a controlled cross-industry set of digital contracts for the demo.
- FR-FD-02: The system shall extract and index contract text in a retrievable knowledge base.
- FR-FD-03: The React UI shall allow the user to submit natural-language questions.
- FR-FD-04: FastAPI shall expose the API contract required by the React UI and agent runtime.
- FR-FD-05: The agent shall retrieve relevant evidence before generating a grounded answer.
- FR-FD-06: The agent shall support clause analysis and comparison across at least two contracts.
- FR-FD-07: Each grounded answer shall expose the document source and supporting excerpt.
- FR-FD-08: If sufficient evidence is not found, the agent shall explicitly abstain.
- FR-FD-09: The UI shall expose the available demo documents and allow document-scoped analysis where applicable.

## 6. Non-Functional Requirements

- NFR-FD-01 Grounding: factual legal claims in the answer must be supported by retrieved evidence.
- NFR-FD-02 Traceability: grounded responses must identify source document and excerpt.
- NFR-FD-03 Usability: the primary flow must not require technical syntax or knowledge of GCP.
- NFR-FD-04 Security basics: credentials and secrets must not be exposed in source code, React bundles or UI.
- NFR-FD-05 Demo latency: standard queries should target <= 15 seconds under demo conditions.
- NFR-FD-06 Minimalism: the UI must keep the primary legal task visually dominant.
- NFR-FD-07 Portability: core legal behavior must remain client-agnostic.
- NFR-FD-08 API clarity: React/FastAPI integration shall use explicit versioned request/response contracts for the demo.

## 7. Acceptance Criteria

### AC-001 — Grounded query
Given contracts are indexed  
When a user asks a question answerable from the corpus  
Then the system returns a relevant answer  
And identifies the source document  
And displays supporting evidence.

### AC-002 — No evidence
Given the requested fact is not supported by the corpus  
When the user asks the question  
Then the system states that sufficient evidence was not found  
And does not fabricate a factual legal answer.

### AC-003 — Clause analysis
Given a contract contains a supported clause type  
When the user asks to analyze that clause  
Then the system locates and summarizes it  
And displays supporting evidence.

### AC-004 — Contract comparison
Given two indexed contracts contain comparable clauses  
When the user asks to compare them  
Then the system summarizes material differences  
And identifies evidence for both documents.

### AC-005 — Evidence verification
Given a grounded answer  
When the user inspects the evidence  
Then the user can identify the source document and supporting excerpt.

### AC-006 — Visible system state
Given a query is submitted  
When processing is in progress  
Then the React UI exposes a visible loading state  
And eventually exposes success, warning, no-evidence or error.

### AC-007 — Cross-industry core
Given the demo is running  
When a user uses any supported demo contract type  
Then the core flow does not depend on a client-specific name, policy, repository or workflow.

### AC-008 — API integration
Given the React application is available  
When it submits a supported request  
Then it communicates with FastAPI through the defined API contract  
And renders the returned answer/evidence without direct model access from the browser.

## 8. Business Rules

- BR-FD-01: The agent may use only the documents enabled for the demo.
- BR-FD-02: Missing evidence must be represented as uncertainty/abstention, not invention.
- BR-FD-03: The agent assists legal analysis; it does not make autonomous legal decisions.
- BR-FD-04: The FAST DEMO runtime is read-only with respect to business systems and source documents.
- BR-FD-05: Client-specific behavior must not be hardcoded into the cross-industry core.
- BR-FD-06: The browser must never call Gemini/Vertex AI directly; model access is mediated by the FastAPI/agent backend.

## 9. Logical Data Model

```text
Document
 ├── document_id
 ├── name
 ├── document_type
 ├── industry_context?   # demo metadata, not client logic
 └──< Chunk
       ├── chunk_id
       ├── content
       ├── section?
       └── metadata

Query
 ├── question
 ├── document_filters?
 └── Response
       ├── answer
       ├── status
       └──< Evidence
             ├── document_id
             ├── chunk_id
             └── excerpt
```

## 10. Integrations

FAST DEMO has no enterprise/client integration dependency.

Runtime boundaries:
- React -> FastAPI
- FastAPI -> Google ADK / agent runtime
- agent runtime -> Vertex AI / Gemini
- agent tools -> lightweight retrieval/knowledge component

## 11. Edge Cases

- Empty query.
- Unsupported legal question.
- No matching evidence.
- One contract missing the requested clause.
- Duplicate/near-duplicate chunks.
- Model timeout.
- Retrieval dependency failure.
- Malformed document.
- Comparison requested with fewer than two valid documents.
- Backend unavailable.
- API returns a controlled error.
- Client-specific question unsupported by the generic corpus.

## 12. Agentic Extension

### Agent Contract

Name: Legal Contract Intelligence Agent

Objective:
Answer contract questions using only evidence retrieved from the enabled cross-industry demo corpus.

May:
- search contract content;
- identify clauses;
- summarize content;
- compare retrieved clauses;
- cite evidence.

Must not:
- invent missing legal facts;
- create or alter contracts;
- approve/reject contracts;
- make autonomous legal decisions;
- use external internet/legal sources for the FAST DEMO;
- execute writes to enterprise systems;
- assume client-specific policies that are not present in the corpus/configuration.

### Tool Contracts

#### search_contracts
Input:
- query
- optional document filters
- top_k

Output:
- document_id
- chunk_id
- excerpt
- relevance score
- metadata

#### get_document
Input:
- document_id

Output:
- document metadata
- retrievable content/chunks needed for analysis

### Knowledge / RAG
- Digital PDF/DOCX only.
- Extract text.
- Prefer contract/section-aware chunks over arbitrary fixed-character splits.
- Preserve document_id, document_name, document_type, chunk_id and section when available.
- Retrieve top-k evidence before model response.
- Always pass evidence into the answer-generation context.

### Memory
No long-term user memory is required for FAST DEMO.
Conversation context may be kept only for the active session if useful.

### Permissions
Read-only.

### Human Approval
Not required for read-only analysis, but the UI must state that outputs support human legal review.

### Evals
Curated golden set of 20-30 questions covering:
- direct lookup;
- clause analysis;
- comparison;
- no-evidence / abstention;
- cross-industry contract types.

### Runtime Limits
- no more than 2 retrieval/document tools;
- no multi-agent delegation;
- bounded top-k retrieval;
- bounded model output suitable for interactive use.

## 13. Definition of Done

The FAST DEMO is complete when a user can:
1. open the deployed React application;
2. see the cross-industry demo contract corpus;
3. ask a contract question;
4. receive a grounded answer through FastAPI + ADK/Gemini;
5. inspect supporting evidence;
6. analyze a clause;
7. compare two contracts;
8. ask an unsupported question and observe a safe abstention;
9. pass the basic Cloud Run smoke test;
10. demonstrate that no client-specific dependency exists in the core flow.
