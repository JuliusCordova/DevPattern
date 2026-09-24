# AWS Component Architecture Profile

## Status

```yaml
platform: aws
review_cadence: weekly
baseline_evidence: OFFICIAL
```

The AWS profile maps DevPattern architecture and Pattern Packs into current AWS managed services.

## Workload profiles

- web-app;
- agentic-app;
- rag;
- event-driven;
- data-platform.

Capability areas reviewed weekly include:

- compute/runtime;
- Amazon Bedrock and agent capabilities;
- knowledge/retrieval;
- relational/NoSQL data;
- S3/data lake;
- messaging/eventing;
- IAM;
- secrets;
- observability;
- networking/private access;
- deployment services.

FAST DEMO should use the smallest deployable combination. Additional services are added only when scale, security, integration or operational requirements justify them.
