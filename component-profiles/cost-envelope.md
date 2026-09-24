# Cost Envelope

A Cost Envelope defines the expected operating-cost boundary for a solution stage.

It is a design constraint, not an accounting forecast.

## Example

```yaml
cost_envelope:
  fast_demo:
    target_monthly_usd: 100
    hard_limit_usd: 200

  mvp:
    target_monthly_usd: 500
    hard_limit_usd: 1000

  product:
    budget_defined_by_business_case: true
```

The amounts above are illustrative. Every project can define its own envelope.

## Why

The Cost Envelope helps the selector avoid architectures that are technically valid but economically inappropriate for the current maturity stage.

## Selector behavior

When an architecture is expected to exceed the Cost Envelope, DevPattern should return alternatives:

```text
Option A — lower cost
Option B — balanced
Option C — higher scale / resilience
```

Each option should explain:

- estimated cost category;
- what capability is gained;
- what risk is reduced;
- what migration path remains;
- why the extra cost is justified.

## Cost categories

When precise pricing is unavailable or unnecessary, use:

- LOW
- MEDIUM
- HIGH

When enough data exists, calculate estimated monthly cost using current platform pricing.

## Governance

The Cost Envelope must be revisited when:

- traffic materially changes;
- data volume changes;
- new regions/environments are introduced;
- availability targets change;
- new integrations appear;
- model consumption changes;
- a managed service changes pricing;
- product stage changes.

## Key rule

> Cost is an architecture metric.
