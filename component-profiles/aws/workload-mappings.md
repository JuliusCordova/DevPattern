# AWS Workload Component Mappings

Status: CURRENT  
Evidence: OFFICIAL  
Review cadence: weekly

Important current note:

> Amazon Bedrock Agents is now **Bedrock Agents Classic** and is not open to new customers. New agentic implementations should evaluate **Amazon Bedrock AgentCore**.

Official reference:
https://docs.aws.amazon.com/bedrock/latest/APIReference/

## 1. Web App

### FAST DEMO
- AWS Lambda + API Gateway for small serverless apps
or
- ECS Fargate for containerized apps
- DynamoDB / Aurora only if persistence is needed

### MVP
- API Gateway
- Lambda or ECS Fargate
- Cognito
- DynamoDB / Aurora
- Secrets Manager
- CloudWatch

### PRODUCT
Add when justified:
- CloudFront
- WAF
- ALB
- multi-AZ data configuration
- private networking
- deployment controls

Official reference:
https://docs.aws.amazon.com/solutions/building-a-containerized-and-scalable-web-application-on-aws/

## 2. Agentic App

### FAST DEMO
- Bedrock model
- simple Lambda / Fargate application
- direct tools

### MVP
- Bedrock
- AgentCore where agent runtime capabilities are needed
- Lambda / ECS Fargate
- IAM roles
- Secrets Manager
- CloudWatch
- explicit tools

### PRODUCT
Add:
- AgentCore Gateway where MCP/tool governance is useful
- permission boundaries
- VPC endpoints/private networking
- persistent state where required
- AgentOps/cost monitoring

## 3. RAG App

### FAST DEMO
- Bedrock
- Bedrock Knowledge Bases
- S3 source

### MVP
- Bedrock Knowledge Bases
- managed or selected vector store
- IAM-filtered access
- retrieval evaluation

Supported vector options may include managed knowledge bases or self-managed stores such as OpenSearch Serverless or Aurora depending requirements.

### PRODUCT
Add:
- AgentCore Gateway for MCP access where useful
- permission-aware retrieval
- ingestion lifecycle
- audit
- benchmark/regression

Official references:
https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base-deploy.html
https://docs.aws.amazon.com/bedrock/latest/userguide/kb-gateway-target.html

## 4. Event-Driven

### FAST DEMO
- EventBridge
- Lambda

### MVP
Choose based on messaging semantics:
- EventBridge for routing/events
- SQS for durable queueing
- SNS for fan-out
- Lambda / ECS consumers

### PRODUCT
Add:
- DLQ
- replay
- cross-account patterns
- idempotency
- CloudWatch alarms/traces

Official reference:
https://docs.aws.amazon.com/decision-guides/latest/decision-guides/sns-or-sqs-or-eventbridge.html

## 5. Data Platform

### FAST DEMO
- S3
- Athena
- Glue only if catalog/ETL is needed

### MVP
- S3 data lake
- Glue catalog/processing
- Athena / Redshift depending analytical workload
- IAM/Lake Formation where governance is required

### PRODUCT
Add:
- Lake Formation governance
- workload isolation
- event ingestion
- DR
- cost controls
- observability

## Default principle

> Start serverless or managed. Add ECS/EKS or complex networking only when the workload demonstrates the need.
