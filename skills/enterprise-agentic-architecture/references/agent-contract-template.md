# Agent Contract Template

Use progressively. FAST DEMO may use only the Lite fields; MVP should complete the relevant sections; PRODUCT should make critical fields machine-readable and enforceable.

```yaml
agent_contract:
  identity:
    agent_id: ""
    name: ""
    owner: ""
    domain: ""
    version: ""
    environment: ""

  purpose:
    outcome: ""
    users: []
    in_scope: []
    out_of_scope: []

  capabilities:
    capability_ids: []
    intents: []
    input_schema: ""
    output_schema: ""

  risk_and_autonomy:
    risk_tier: ""
    autonomy_tier: "A0|A1|A2|A3|A4"
    allowed_actions: []
    forbidden_actions: []

  data:
    classifications: []
    allowed_sources: []
    residency: ""
    retention: ""
    freshness_slo: ""

  knowledge:
    strategies: ["RAG"]
    authoritative_sources: []
    provenance_required: true
    evidence_required: true

  context_and_memory:
    required_context: []
    allowed_context: []
    forbidden_context: []
    cross_domain_sharing: ""
    memory_policy: ""

  tools:
    allowed_tools: []
    allowed_mcp_servers: []
    scopes: []
    write_actions: []

  models:
    approved_model_policies: []
    routing_policy: ""
    fallback_policy: ""

  trust:
    correctness_threshold: ""
    groundedness_threshold: ""
    abstention_policy: ""
    evidence_coverage_threshold: ""

  human_oversight:
    approval_required_for: []
    approver_roles: []
    segregation_of_duties: []
    escalation_path: ""

  operations:
    slo: ""
    timeout: ""
    retry_policy: ""
    concurrency_limit: ""
    budget: ""

  observability:
    required_trace_fields: []
    eval_suites: []
    security_events: []
    business_outcomes: []

  lifecycle:
    status: "draft"
    certification: ""
    expires_at: ""
    next_review: ""
    rollback_target: ""
```

## Lite contract

At minimum capture:
- owner;
- purpose/outcome;
- allowed data;
- approved model;
- allowed tools;
- forbidden actions;
- acceptance/golden cases.

## Promotion rule

A contract is not a static document. Any material change in model policy, tool permissions, data classification, autonomy, knowledge source or risk may trigger re-evaluation and recertification.
