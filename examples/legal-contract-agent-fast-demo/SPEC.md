# FAST DEMO SPEC — Legal Contract Agent on GCP

Status: Draft for implementation  
Maturity: FAST DEMO  
Cloud: Google Cloud  
Pattern baseline: PA-SDD + GCP FAST DEMO

## 1. Business Intent

### Problem
Legal users spend time reviewing contracts manually to answer focused questions about clauses, obligations, penalties, validity, confidentiality and differences across documents.

### Desired Outcome
Demonstrate that a legal user can ask natural-language questions over a controlled set of contracts and receive grounded, traceable answers supported by source evidence.

### Success Metric
For a curated demo set:
- answer correctness >= 80%
- evidence correctness >= 90%
- unsupported answer rate <= 10%

## 2. Scope

### In Scope
- Controlled corpus of digital PDF/DOCX contracts.
- Text extraction and chunking.
- Querying contracts in natural language.
- Clause analysis.
- Comparison of at least two contracts.
- Source evidence in each grounded answer.
- Explicit abstention when evidence is insufficient.
- Functional UI deployed on GCP.
- Basic smoke validation.

### Out of Scope
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

### Legal Specialist
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

- FR-FD-01: The system shall load a controlled set of digital contracts for the demo.
- FR-FD-02: The system shall extract and index contract text in a retrievable knowledge base.
- FR-FD-03: The user shall be able to submit natural-language questions.
- FR-FD-04: The agent shall retrieve relevant evidence before generating a grounded answer.
- FR-FD-05: The agent shall support clause analysis and comparison across at least two contracts.
- FR-FD-06: Each grounded answer shall expose the document source and supporting excerpt.
- FR-FD-07: If sufficient evidence is not found, the agent shall explicitly abstain.

## 6. Non-Functional Requirements

- NFR-FD-01 Grounding: factual legal claims in the answer must be supported by retrieved evidence.
- NFR-FD-02 Traceability: grounded responses must identify source document and excerpt.
- NFR-FD-03 Usability: the primary flow must not require technical syntax or knowledge of GCP.
- NFR-FD-04 Security basics: credentials and secrets must not be exposed in source code or UI.
- NFR-FD-05 Demo latency: standard queries should target <= 15 seconds under demo conditions.
- NFR-FD-06 Minimalism: the UI must keep the primary legal task visually dominant.

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
Then the UI exposes a visible loading state  
And eventually exposes success, warning, or error.

## 8. Business Rules

- BR-FD-01: The agent may use only the documents enabled for the demo.
- BR-FD-02: Missing evidence must be represented as uncertainty/abstention, not invention.
- BR-FD-03: The agent assists legal analysis; it does not make autonomous legal decisions.
- BR-FD-04: The FAST DEMO runtime is read-only with respect to business systems and source documents.

## 9. Logical Data Model

```text
Document
 ├── document_id
 ├── name
 ├── document_type
 └──< Chunk
       ├── chunk_id
       ├── content
       ├── section?
       └── metadata

Query
 └── Response
       └──< Evidence
             ├── document_id
             ├── chunk_id
             └── excerpt
```

## 10. Integrations

FAST DEMO has no enterprise integration dependency.

Primary runtime integrations:
- Vertex AI / Gemini
- local or lightweight vector/retrieval component used by the demo runtime

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

## 12. Agentic Extension

### Agent Contract

Name: Legal Contract Agent

Objective:
Answer contract questions using only evidence retrieved from the enabled demo corpus.

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
- execute writes to enterprise systems.

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
- Chunk into contract-relevant segments.
- Preserve document_id, document_name, chunk_id and section when available.
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
- no-evidence / abstention.

### Runtime Limits
- no more than 2 retrieval/document tools;
- no multi-agent delegation;
- bounded top-k retrieval;
- bounded model output suitable for interactive use.

## 13. Definition of Done

The FAST DEMO is complete when a user can:
1. open the deployed application;
2. see the demo contract corpus;
3. ask a contract question;
4. receive a grounded answer;
5. inspect supporting evidence;
6. analyze a clause;
7. compare two contracts;
8. ask an unsupported question and observe a safe abstention;
9. pass the basic Cloud Run smoke test.
