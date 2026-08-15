# Terraform Cost Guardrail Pipeline

## Overview
A CI/CD pipeline that estimates and validates Terraform costs before applying changes, preventing budget overruns and unexpected cloud bills.

## Architecture
```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   PR        │    │  Cost       │    │  Approval   │
│  (GitHub)   │───▶│  Estimator  │───▶│  Gate       │
└─────────────┘    └─────────────┘    └─────────────┘
                                        │
                                   ┌───────────┐
                                   │  Apply    │
                                   │  (if OK)  │
                                   └───────────┘
```

## Workflow
1. **Trigger**: Pipeline activates on PR to infrastructure repo
2. **Estimate**: Run `terraform plan` + cost estimation tool (CloudZero, Terratest, or custom)
3. **Validate**: Compare estimated cost against budget thresholds
4. **Report**: Post cost analysis as PR comment
5. **Gate**: Require approval if cost exceeds threshold
6. **Apply**: Execute terraform apply on merge

## Tools
- Terraform
- GitHub Actions / GitLab CI
- cloud-cfn-nag or infracost for cost estimation
- AWS/Azure/GCP cost APIs
- Python for custom validation logic

## Learning Goals
- Master Terraform cost estimation techniques
- Learn CI/CD pipeline design for IaC
- Understand cloud pricing models
- Practice budget governance in DevOps

## Build Milestones
1. **M1**: Basic `terraform plan` with cost annotation
2. **M2**: Integrate infracost for detailed breakdown
3. **M3**: Add budget threshold validation
4. **M4**: Create PR comment with cost comparison
5. **M5**: Implement approval workflow for over-budget changes
6. **M6**: Add historical cost trending and alerts
