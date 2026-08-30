# Terraform Plan Anomaly Detector with Drift Analysis

## Overview
A tool that analyzes Terraform plans to detect anomalies—unexpected resource changes, cost spikes, or security regressions—before they're applied. Uses statistical baseline comparison and LLM-based explanation generation.

## Architecture / Structure
- **Plan Parser**: Extracts diff information from `terraform plan -out`
- **Baseline Comparator**: Compares current plan against historical plan patterns
- **Cost Estimator**: Calculates price difference using cloud pricing APIs
- **Security Scanner**: Checks for permission escalations or exposed resources
- **Explanation Generator**: Natural language summary of what changed and why

## Workflow
1. Run Terraform plan and capture JSON output
2. Parse resource additions, modifications, deletions
3. Compare against last N plans to establish baseline
4. Flag anomalous changes (e.g., sudden security group open to 0.0.0.0/0)
5. Estimate cost impact using AWS/Azure pricing endpoints
6. Generate plain-language explanation for human review
7. Block apply if critical anomalies detected

## Tools
- Terraform JSON plan parser
- AWS Pricing API / Azure REST API for cost estimation
- Python with regex for change detection
- Ollama + local LLM for explanation generation
- GitHub Actions for CI/CD integration

## Learning Goals
- Terraform internals and plan format
- Cloud provider pricing structures
- Anomaly detection in configuration changes
- Security best practices for IaC

## Build Milestones
1. Week 1: Terraform plan JSON parsing and diff extraction
2. Week 2: Baseline storage and comparison logic
3. Week 3: Cost estimation integration with cloud APIs
4. Week 4: Security rule checking (overly permissive rules)
5. Week 5: LLM-powered explanation generation
6. Week 6: Pre-commit hook and GitHub Action deployment
