# Pack — Memory

## Intent

Persist information across turns or sessions when prior context materially improves future outcomes.

## Separate memory types

- **Session state** — current conversation/workflow.
- **Profile/preferences** — stable user-specific context.
- **Episodic memory** — prior relevant interactions or outcomes.
- **Domain knowledge** — belongs in RAG/knowledge stores, not user memory.

## Use when

- multi-turn continuity is necessary;
- preferences materially affect decisions;
- long-running tasks must resume;
- prior outcomes improve future execution.

## Avoid when

Stateless behavior is sufficient.

## FAST
- in-session context only.

## MVP
- explicit memory schema;
- read/write rules;
- expiration strategy;
- memory evals.

## PRODUCT
- tenant/user isolation;
- consent and retention policies;
- deletion/update handling;
- provenance;
- sensitive-data controls;
- compaction/summarization strategy.

## Key rule

Store the minimum durable memory required for the product outcome.
