# IaC Generator from Natural Language

**Category:** Combined  
**Date:** 2026-08-31

## Overview
A tool that takes natural language descriptions of infrastructure and generates valid Terraform or Pulumi code. Supports multiple cloud providers and best-practice patterns.

## Architecture
```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  Natural        │────▶│  LLM Generator  │────▶│  Validation    │
│  Language Input │     │                 │     │  & Linting     │
└─────────────────┘     └─────────────────┘     └────────┬────────┘
                                                        │
                                              ┌────────▼────────┐
                                              │  Terraform /   │
                                              │  Pulumi Output │
                                              └─────────────────┘
```

## Workflow
1. User describes infrastructure in plain English
2. LLM generates initial IaC code
3. Validate against provider schemas
4. Lint for security and best practices
5. Refine based on feedback
6. Output ready-to-apply configuration

## Tools
- Python
- OpenRouter or Ollama for LLM
- Terraform/Pulumi SDKs for validation
- Sentinel or OPA for policy checking

## Learning Goals
- Infrastructure as Code patterns
- LLM prompt engineering for code generation
- Validation and linting pipelines
- Multi-cloud abstraction

## Build Milestones
- [ ] Week 1: Basic Terraform generation from prompts
- [ ] Week 2: Multi-provider support (AWS, GCP, Azure)
- [ ] Week 3: Validation against Terraform schema
- [ ] Week 4: Security linting and policy checks
- [ ] Week 5: Iterative refinement with user feedback
- [ ] Week 6: CLI tool with plan/apply workflow
