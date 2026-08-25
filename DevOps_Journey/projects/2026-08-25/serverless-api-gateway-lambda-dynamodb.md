# Project: Serverless API Gateway with AWS Lambda and DynamoDB

## Overview
Build a serverless REST API on AWS using API Gateway, Lambda functions, and DynamoDB. Implement authentication with Cognito, rate limiting, request validation, and automated deployment via Terraform. Design for high availability and auto-scaling with zero server management.

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│  Client (mobile/web app)                            │
│       │                                              │
│       ▼                                              │
│  ┌──────────────────────────────────────────────┐   │
│  │  Amazon Cognito (User Pool + Auth)           │   │
│  └──────────────────────────────────────────────┘   │
│       │                                              │
│       ▼                                              │
│  ┌──────────────────────────────────────────────┐   │
│  │  API Gateway (REST API)                       │   │
│  │  ├── /tasks     GET / POST                    │   │
│  │  ├── /tasks/{id} GET / PUT / DELETE           │   │
│  │  └── Stage vars + Throttling                  │   │
│  └──────────────────────────────────────────────┘   │
│       │                                              │
│       ▼                                              │
│  ┌──────────────────────────────────────────────┐   │
│  │  Lambda Functions (Python/Node.js)            │   │
│  │  ├── list_tasks.py                             │   │
│  │  ├── create_task.py                            │   │
│  │  └── delete_task.py                            │   │
│  └──────────────────────────────────────────────┘   │
│       │                                              │
│  ┌────▼─────────────────────────────────────┐       │
│  │  DynamoDB Table: Tasks                    │       │
│  │  ├── PK: userId                          │       │
│  │  ├── SK: taskId                          │       │
│  │  └── GSI: status + createdAt             │       │
│  └──────────────────────────────────────────┘        │
├─────────────────────────────────────────────────────┤
│  Terraform (IaC)                                    │
│  └── modules/                                         │
│      ├── api_gateway/                                 │
│      ├── lambda/                                      │
│      ├── dynamodb/                                    │
│      └── cognito/                                     │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Write Terraform modules for each AWS resource
2. Define DynamoDB table with partition key (userId) and sort key (taskId)
3. Create Lambda functions with proper IAM roles; deploy via Terraform
4. Configure API Gateway methods and integrations with Lambda
5. Add Cognito user pool for JWT authentication
6. Enable API Gateway usage plans with API keys for rate limiting
7. Set up CloudWatch Logs and Alarms for Lambda errors
8. Add CDK or Serverless Framework alternative comparison

## Tools
- **Terraform** (infrastructure as code)
- **AWS Lambda** (compute)
- **Amazon API Gateway** (HTTP endpoint)
- **DynamoDB** (NoSQL database)
- **Amazon Cognito** (authentication)
- **AWS CloudWatch** (monitoring)
- **Postman** (API testing)

## Learning Goals
- Serverless architecture patterns and trade-offs
- DynamoDB design: partition keys, sort keys, GSIs, capacity modes
- Lambda cold starts and provisioned concurrency
- API Gateway throttling and usage plans
- Cognito integration with JWT tokens in API Gateway
- Terraform state management for multi-environment AWS infra

## Build Milestones
1. [ ] Provision DynamoDB table with Terraform; verify CRUD operations
2. [ ] Write and deploy 3 Lambda functions (list, create, delete tasks)
3. [ ] Create REST API Gateway with Lambda proxy integration
4. [ ] Set up Cognito user pool; add authorizer to API Gateway
5. [ ] Configure usage plan with rate limit (100 req/min)
6. [ ] Add CloudWatch alarms for Lambda throttles and errors
7. [ ] Test full flow with Postman; document API contract
8. [ ] Deploy to staging; compare cost vs. EC2 baseline

## References
- https://docs.aws.amazon.com/lambda/latest/dg/services-apigateway.html
- https://registry.terraform.io/providers/hashicorp/aws/latest/docs
