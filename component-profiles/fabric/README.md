# Microsoft Fabric Component Architecture Profile

Microsoft Fabric is treated as a distinct profile rather than merely a sub-section of Azure because it provides an integrated data and analytics operating model.

## Status

```yaml
platform: microsoft-fabric
review_cadence: weekly
baseline_evidence: OFFICIAL
```

## Workload profiles

- lakehouse;
- medallion;
- real-time;
- semantic-layer;
- AI/data consumption.

## Typical architecture progression

```text
Sources
  ↓
Data Factory / Mirroring / Eventstream
  ↓
OneLake
  ↓
Bronze
  ↓
Silver
  ↓
Gold
  ↓
Semantic Model
  ↓
Power BI / AI / Agents
```

The exact services are reviewed weekly because Fabric capabilities evolve quickly.

The Medallion pattern remains a stable pattern. The Fabric components used to implement it may change.
