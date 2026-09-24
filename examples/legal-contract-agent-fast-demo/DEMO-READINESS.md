# Demo Readiness — Legal Contract Agent

## Reusable lesson from ATLAS DataGob

A demo should be repeatable, stable and based on versioned curated data rather than hardcoded behavior.

## Required demo assets

- curated contract corpus;
- golden question set;
- optional reset/reindex command;
- health endpoint;
- smoke test;
- short demo script;
- known limitations.

## Recommended demo script

1. Open the application.
2. Ask a direct factual question.
3. Inspect source evidence.
4. Ask for a clause analysis.
5. Compare the same clause across two contracts.
6. Ask a question not supported by the corpus.
7. Show the safe abstention.
8. Optionally show the golden-set summary.

## Smoke checks

Non-destructive by default:

- API/runtime health is OK.
- UI is reachable.
- UI can call the agent runtime.
- corpus/retrieval service is reachable.
- one known grounded query succeeds.
- no-evidence query returns a safe result.

Any reindex/reset that mutates demo state should be explicit and opt-in.
