# Pack — Evaluation & Observability

## Intent

Make agent quality measurable before release and behavior diagnosable after release.

## Two complementary loops

```text
OFFLINE
Dataset → Run → Grade → Compare → Fix

ONLINE
Production Trace → Detect Failure → Review → New Eval → Regression
```

## What to capture

- model calls;
- tool calls;
- handoffs;
- latency;
- errors;
- token/cost usage;
- guardrail outcomes;
- task/business outcome;
- agent/version/prompt/model identifiers.

## FAST
- 5–10 critical scenarios;
- manual trace inspection;
- smoke metrics.

## MVP
- versioned golden dataset;
- tool/routing metrics;
- trace grading;
- latency/token monitoring;
- regression run before merge/release.

## PRODUCT
- online monitoring;
- failure clustering;
- production traces → eval dataset;
- SLOs;
- cost per successful outcome;
- alerting;
- privacy-aware content capture;
- release quality gates.

## Key rule

> Every meaningful production failure should become a regression case.
