# Terraform Multi-Cloud Infrastructure with Drift Detection

## Overview
Create a Terraform-based infrastructure that spans AWS and Azure, with automated drift detection to identify when manual changes occur.

## Architecture
```
Terraform State (S3 + DynamoDB)
     ↓
AWS Resources ←→ Azure Resources
     ↓
Drift Detection Job (GitHub Actions)
     ↓
Alerts (Slack/Email)
```

## Workflow
1. Define infrastructure as code for both clouds
2. Set up remote state with locking
3. Create daily drift detection job
4. Implement auto-remediation for non-critical changes
5. Generate compliance reports

## Tools & Stack
- Terraform, AWS CLI, Azure CLI
- GitHub Actions for CI/CD
- S3 + DynamoDB for state management
- Slack webhook for alerts

## Learning Goals
- Multi-cloud Terraform patterns
- State management and locking
- Infrastructure drift detection
- Cross-cloud networking basics

## Build Milestones
1. **Week 1**: Terraform basics + AWS setup
2. **Week 2**: Add Azure provider and resources
3. **Week 3**: Implement remote state with locking
4. **Week 4**: Build drift detection workflow
5. **Week 5**: Add remediation and reporting
