# FAST DEMO Evals — Legal Contract Agent

## Goal

Provide enough executable evidence to decide whether the demo proves the intended legal-assistant behavior.

## Golden dataset

Create 20-30 curated questions across these groups:

| Group | Suggested count | Expected behavior |
|---|---:|---|
| Direct factual lookup | 8 | answer + correct source evidence |
| Clause analysis | 6 | identify/summarize clause + evidence |
| Contract comparison | 6 | compare two sources + evidence for both |
| No evidence | 4 | explicit abstention |
| Adversarial/ambiguous | 3-6 | safe bounded answer or abstention |

Each case should contain:

```yaml
id:
question:
documents_expected:
answer_expectation:
evidence_expectation:
must_abstain: false
notes:
```

## Minimum metrics

### Answer correctness
Target: >= 80%

Human-reviewed against the expected business answer.

### Evidence correctness
Target: >= 90%

The cited/revealed excerpt must actually support the generated claim.

### Unsupported answer rate
Target: <= 10%

A response is unsupported when it states a legal fact not evidenced by the enabled corpus.

### Abstention correctness
No-evidence cases should abstain rather than invent.

### Latency
Capture end-to-end response time for demo queries.

## Eval policy

- Do not hide failed examples.
- A retrieval miss and a reasoning miss must be recorded separately when possible.
- The golden set is versioned with the demo.
- New observed failures become new regression cases.
- FAST DEMO acceptance is evidence-based, not based only on a successful live presentation.
