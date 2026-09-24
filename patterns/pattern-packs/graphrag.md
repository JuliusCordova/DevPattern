# Pack — GraphRAG

## Intent

Use graph structure when retrieval must reason over entities, relationships, communities, or global themes across a corpus.

Microsoft GraphRAG builds a knowledge graph, community hierarchy, and community summaries before query-time retrieval.

## Use when

- questions span multiple documents;
- relationships between entities are critical;
- global corpus-level questions matter;
- ordinary chunk similarity misses relational context;
- discovery of communities/themes is valuable.

## Avoid when

Do not use GraphRAG merely because a graph database exists.

Prefer conventional RAG when:
- queries are primarily local factual lookup;
- hybrid retrieval already performs well;
- corpus is small;
- indexing cost/complexity is not justified.

## Reference flow

```text
Documents
  ↓
Entity / Relation Extraction
  ↓
Knowledge Graph
  ↓
Community Detection
  ↓
Community Summaries
  ↓
Query Router
   ├─ Local / entity query
   └─ Global / community query
  ↓
Grounded Synthesis
```

## FAST
- GraphRAG only for a clearly relational demo;
- subset corpus;
- a few local/global benchmark questions.

## MVP
- explicit graph schema or extraction strategy;
- entity-resolution checks;
- local vs global query evaluation;
- comparison against baseline RAG.

## PRODUCT
- incremental graph updates;
- lineage/provenance;
- permission-aware graph access;
- graph quality monitoring;
- cost-controlled indexing;
- baseline regression against simpler RAG.

## Required decision gate

GraphRAG must demonstrate measurable improvement over conventional RAG on representative questions before promotion.

## Key rule

GraphRAG is a specialization for relational and global reasoning, not the default retrieval architecture.
