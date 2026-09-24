# Demo Readiness — Cross-Industry Legal Contract Intelligence

## Principle

The demo must be repeatable, stable, client-agnostic and based on versioned curated/synthetic data rather than hardcoded behavior.

## Required demo assets

- cross-industry curated/synthetic contract corpus;
- golden question set;
- optional reset/reindex command;
- FastAPI health endpoint;
- smoke test;
- short demo script;
- known limitations.

Recommended corpus categories:
- services agreement;
- supplier agreement;
- NDA/confidentiality;
- technology agreement;
- lease agreement;
- consulting agreement.

## Recommended demo script

1. Open the React application.
2. Select or inspect available contracts.
3. Ask a direct factual question.
4. Inspect source evidence.
5. Ask for a clause analysis.
6. Compare the same clause across two contracts.
7. Ask a question not supported by the corpus.
8. Show the safe abstention.
9. Optionally show the golden-set summary.

## Smoke checks

Non-destructive by default:

- FastAPI /health is OK.
- React UI is reachable.
- React can call FastAPI.
- FastAPI can invoke the agent runtime.
- corpus/retrieval service is reachable.
- one known grounded query succeeds.
- no-evidence query returns a safe result.
- no client-specific dependency is required for the primary flow.

Any reindex/reset that mutates demo state must be explicit and opt-in.
