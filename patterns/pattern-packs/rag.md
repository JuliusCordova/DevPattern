# Pack — RAG

## Intent

Ground model responses in external knowledge retrieved at runtime.

## Preferred retrieval flow

```text
Documents
  ↓
Parse / Normalize
  ↓
Chunk + Metadata
  ↓
Embeddings / Index
  ↓
Hybrid Retrieval
  ↓
Optional Reranking
  ↓
Context Assembly
  ↓
LLM
  ↓
Cited Answer
```

## Use when

- knowledge changes independently from the model;
- private/domain content is required;
- traceable sources matter;
- corpus does not fit safely in prompt context.

## Core practices

- evaluate chunking rather than assuming one universal size;
- preserve metadata and document identity;
- prefer hybrid keyword + vector retrieval when useful;
- add reranking only when measured relevance improves enough to justify latency;
- return a small relevant context set rather than flooding the model;
- support metadata filtering;
- require source attribution for grounded answers.

## FAST
- small corpus;
- managed vector store allowed;
- basic semantic retrieval;
- 5–10 test questions.

## MVP
- chunking strategy;
- hybrid retrieval;
- metadata filters;
- retrieval metrics;
- groundedness/citation evals.

## PRODUCT
- ingestion lifecycle;
- ACL/permission-aware retrieval;
- hybrid + reranking when justified;
- freshness/lineage;
- retrieval observability;
- regression dataset.

## Key metrics

- Recall@K
- Precision@K
- groundedness
- citation correctness
- answer correctness
- latency
- cost per successful answer

## Key rule

Retrieval quality is part of the product, not infrastructure plumbing.
