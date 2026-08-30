# IaC Generator from Natural Language

## Overview
Convert natural language descriptions of infrastructure into production-ready Terraform, Pulumi, or Crossplane manifests. Supports multi-cloud and validates generated configs against best practices before output.

## Architecture / Structure
- **Intent Parser**: Extracts infrastructure requirements from natural language
- **Template Selector**: Chooses appropriate IaC template based on target cloud/provider
- **Generator**: Produces valid manifest code with proper structure
- **Validator**: Checks generated code for security, cost, and compliance issues
- **Formatter**: Styles output according to provider-specific conventions
- **Diff Preview**: Shows proposed changes against existing state

## Supported Outputs
- Terraform HCL for AWS, Azure, GCP
- Pulumi Python/TypeScript
- Crossplane composite resources
- Kustomize overlays for Kubernetes
- Ansible playbooks for configuration management

## Workflow
1. User describes infrastructure: "VPC with public/private subnets, RDS MySQL, ALB, and auto-scaling group"
2. Intent parser identifies components and relationships
3. Template selector matches to most appropriate scaffold
4. Generator fills in parameters and creates connections
5. Validator runs security and cost checks
6. User reviews diff and applies changes
7. Generated code committed to repository

## Tools
- Ollama with structured output capabilities
- Terraform/Pulumi SDKs for validation
- Conftest for policy checking
- GitHub Copilot or similar for code completion
- Markdown templates for common patterns

## Learning Goals
- Infrastructure-as-code patterns and anti-patterns
- Multi-cloud architecture design
- LLM structured output for code generation
- Validation and policy enforcement for IaC
- GitOps workflow integration

## Build Milestones
1. Week 1: Intent parser with pattern matching for common infra types
2. Week 2: Terraform HCL generation with variable substitution
3. Week 3: Multi-cloud provider support and template library
4. Week 4: Validation pipeline with security rule checking
5. Week 5: Diff preview and change summary generation
6. Week 6: GitOps integration with auto-commit and PR creation
