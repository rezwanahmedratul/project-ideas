# DevOps: Terraform Plan Predictor

## Overview
Create a tool that analyzes Terraform plans and predicts potential issues before they reach production — resource conflicts, cost overruns, security misconfigurations, and compliance violations — using static analysis combined with historical drift data.

## Architecture
```
Terraform Plan JSON → Plan Analyzer Engine
                          ├── Cost Estimator (pricing API)
                          ├── Security Scanner (policy-as-code)
                          ├── Conflict Detector (state diff analysis)
                          └── Drift Predictor (historical pattern ML)
```

## Workflow
1. Run `terraform plan -out=tfplan`
2. Convert plan to JSON and feed to analyzer
3. Each dimension runs in parallel
4. Aggregated report with severity scores and remediation suggestions

## Tools
Terraform, Python, AWS Pricing API, OPA/Gatekeeper, Redis (drift history)

## Learning Goals
- Terraform state and plan internals
- Policy-as-code enforcement
- Cloud cost estimation models
- Static analysis for infrastructure-as-code

## Build Milestones
1. Parse and visualize Terraform plan JSON
2. Integrate cloud pricing APIs for cost prediction
3. Build security policy checker (CIS benchmarks)
4. Add drift prediction using historical state diffs
5. Create a GitHub Action wrapper for CI integration
