# Architecture Patterns

DevPattern treats software architecture as a reusable engineering decision, not as mandatory ceremony.

Architecture must remain **proportional to product maturity, integration complexity, business criticality, and expected change**.

> Use the simplest architecture that protects the next stage of the product.

## Default decision principle

```text
Can a simple structure solve the problem clearly?
        │
       YES
        ▼
   Keep it simple
        │
        └──────────────┐
                       │ complexity grows
                       ▼
             Introduce explicit boundaries
                       │
                       ▼
              Hexagonal + Vertical Slice
```

## Recommended patterns

- **Simple Feature Slice** — preferred for FAST demos and small applications.
- **Hexagonal Slice Architecture** — preferred for MVP and PRODUCT workloads with meaningful domain logic, integrations, agent tools, vendor dependencies, or higher change/risk.

Hexagonal Slice is a recommendation, not a universal requirement.

## Anti-overengineering rule

Do not create an abstraction only because a pattern says one could exist.

Create a port, adapter, interface, policy layer, or additional boundary when at least one of these conditions is true:

- a meaningful external dependency must be isolated;
- a second implementation is likely or already exists;
- the dependency is volatile or vendor-specific;
- the boundary materially improves testing;
- security or permission separation requires it;
- different teams or slices must evolve independently;
- the business rule must remain independent from technical infrastructure.

Otherwise, prefer the simpler implementation.
