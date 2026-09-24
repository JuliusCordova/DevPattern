# Microsoft Fabric Data Agent Reference Architecture

Status: CURRENT  
Evidence: OFFICIAL  
Review cadence: weekly

Fabric is treated as a **data-agent / conversational analytics** architecture, not as a general-purpose agent runtime for all software.

## FAST DEMO

```mermaid
flowchart LR
    U[User] --> DA[Fabric Data Agent]
    DA --> S[Curated Data Source]
    S --> LH[Lakehouse]
    S --> WH[Warehouse]
    S --> SM[Semantic Model]
```

Minimum:
- one curated source
- basic instructions
- representative questions

## MVP

```mermaid
flowchart TB
    U[User / Power BI / Copilot Surface] --> DA[Fabric Data Agent]
    DA --> SEM[Semantic Layer]
    SEM --> LH[Lakehouse]
    SEM --> WH[Warehouse]
    SEM --> KQL[KQL / Eventhouse]
    LH --> OL[OneLake]
    WH --> OL
    KQL --> OL
    DA --> INS[Instructions / Topics / Examples]
    DA --> EVAL[Evaluation Dataset]
```

Add:
- curated semantic model
- source descriptions
- example queries
- evaluation dataset
- ownership

## PRODUCT

```mermaid
flowchart TB
    CH[Enterprise Channel] --> DA[Governed Fabric Data Agent]
    DA --> RT[Standard Runtime]
    RT --> SEM[Governed Semantic Layer]
    SEM --> LH[Lakehouse]
    SEM --> WH[Warehouse]
    SEM --> KQL[KQL / Eventhouse]
    LH --> OL[OneLake]
    WH --> OL
    KQL --> OL
    OL --> GOV[Lineage / Governance / Monitoring]
    GOV --> SEC[RLS / OLS / Ownership]
```

Add:
- standard runtime for production stability
- semantic ownership
- governed sources
- RLS/OLS where relevant
- lineage
- monitored runtime

## Key rule

> Fabric Data Agent is the agentic consumption layer for governed data; it is not the default runtime for general-purpose application agents.
