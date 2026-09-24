# Microsoft Fabric Workload Component Mappings

Status: CURRENT  
Evidence: OFFICIAL  
Review cadence: weekly

Fabric is treated as a **data and analytics platform profile**, not as the default general-purpose web application runtime.

## 1. Lakehouse / Data Platform

### FAST DEMO
- OneLake
- Lakehouse
- manual upload / shortcut / simple notebook

### MVP
- OneLake
- Lakehouse
- Data Factory pipelines or Dataflow Gen2
- notebooks/Spark where needed
- Bronze / Silver / Gold
- semantic model

### PRODUCT
Add:
- governed workspaces/domains
- deployment pipelines
- Purview integration where applicable
- capacity monitoring
- DR/recovery planning
- data quality and lineage

Official reference:
https://learn.microsoft.com/en-us/fabric/data-engineering/load-data-lakehouse

## 2. Medallion

### FAST DEMO
- Lakehouse
- Bronze / Silver / Gold folders/tables
- simple notebook/SQL transforms

### MVP
- orchestrated ingestion
- Delta tables
- explicit data quality rules
- semantic Gold layer

### PRODUCT
Add:
- domain ownership
- lineage
- governed promotion
- recovery/reprocessing
- capacity/FinOps controls

## 3. Real-Time

### FAST DEMO
- Eventstream
- Lakehouse or Eventhouse

### MVP
- Real-Time hub
- Eventstream
- Eventhouse
- KQL
- dashboard / alerts

### PRODUCT
Add:
- reliability/recovery design
- workload monitoring
- retry behavior
- secondary capacity strategy where justified

Official references:
https://learn.microsoft.com/en-us/fabric/real-time-intelligence/
https://learn.microsoft.com/en-us/fabric/real-time-intelligence/eventhouse-reliability

## 4. Semantic / BI

### FAST DEMO
- Lakehouse/Warehouse
- semantic model
- Power BI

### MVP
- Direct Lake semantic model
- measures
- relationships
- governed metric definitions

### PRODUCT
Add:
- semantic model ownership
- deployment lifecycle
- RLS/OLS as required
- monitoring
- lineage

Official reference:
https://learn.microsoft.com/en-us/fabric/data-engineering/tutorial-build-lakehouse

## 5. Conversational Data / Agentic Consumption

### FAST DEMO
- Fabric Data Agent
- one curated source

### MVP
- Fabric Data Agent
- curated Lakehouse/Warehouse/semantic model/KQL source
- source descriptions
- instructions
- example queries
- evaluation dataset

### PRODUCT
Add:
- security/governance review
- deployment lifecycle
- monitored runtime
- semantic ownership
- approved data sources

Fabric Data Agent can answer questions over lakehouses, warehouses, semantic models, KQL databases, ontologies, and Microsoft Graph in Fabric.

Official references:
https://learn.microsoft.com/en-us/fabric/data-science/how-to-create-data-agent
https://learn.microsoft.com/en-us/fabric/data-science/data-agent-runtime

## Default principle

> Use Fabric for integrated data/analytics workloads. Use Azure application runtimes for general-purpose application hosting unless Fabric itself is the product surface.
