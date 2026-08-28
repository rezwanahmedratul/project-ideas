# Combined: Infrastructure as Code Generator from Natural Language

## Overview
Build a tool that takes natural language descriptions of infrastructure requirements and generates production-ready Terraform, Pulumi, or CDK code — with AI validating the generated code against best practices and cloud provider constraints.

## Architecture
```
Natural Language Input → LLM Code Generator
                                       ├── Template Engine (Terraform/Pulumi/CDK)
                                       ├── Validator (checkov, tfsec, cdk-nag)
                                       ├── Cost Estimator (cloud pricing APIs)
                                       └── Review Assistant (suggestions for improvement)
                                       ↓
                               Generated IaC Code
```

## Workflow
1. User describes infrastructure needs in plain English
2. LLM generates initial IaC code in chosen framework
3. Validator runs security and best-practice checks
4. Cost estimator provides monthly cost projection
5. Human reviews and iterates; final code committed to repo

## Tools
Python, Claude API / o3-mini, Terraform / Pulumi / CDK, checkov, tfsec, AWS Pricing API, GitHub

## Learning Goals
- Infrastructure-as-code generation patterns
- LLM prompt engineering for code synthesis
- Security policy validation for IaC
- Cloud cost estimation from code

## Build Milestones
1. Build prompt templates for common infrastructure patterns
2. Generate Terraform code from natural language input
3. Integrate checkov/tfsec for security validation
4. Add AWS/GCP cost estimation from generated resources
5. Create interactive refinement loop (user feedback → regenerated code)
