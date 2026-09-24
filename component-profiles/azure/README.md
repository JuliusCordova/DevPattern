# Azure Component Architecture Profile

## Status

```yaml
platform: azure
review_cadence: weekly
baseline_evidence: OFFICIAL
```

The Azure profile maps vendor-neutral DevPattern patterns into current Azure components.

## Workload profiles

- web-app;
- agentic-app;
- rag;
- event-driven;
- data-platform.

Typical capability areas to evaluate weekly include:

- application/container runtime;
- Azure AI / agent runtime;
- model serving;
- AI Search / retrieval;
- relational and NoSQL data;
- messaging and events;
- Managed Identity / Entra ID;
- Key Vault;
- Monitor / Application Insights;
- networking/private access.

The profile must prefer the smallest viable component set for FAST DEMO and introduce enterprise controls progressively.
