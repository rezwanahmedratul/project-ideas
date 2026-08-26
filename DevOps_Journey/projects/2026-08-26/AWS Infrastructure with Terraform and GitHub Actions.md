# AWS Infrastructure with Terraform & GitHub Actions

## Overview
Create a complete AWS infrastructure deployment pipeline using Terraform for IaC and GitHub Actions for CI/CD.

## Architecture
```
GitHub → Terraform Plan → Review → Terraform Apply → AWS
                    ↓
              State Locking (DynamoDB)
```

## Workflow
1. Set up GitHub repo with Terraform code
2. Configure Terraform workspace strategy
3. Create GitHub Actions workflow
4. Implement plan/apply separation
5. Add state locking and remote backend

## Tools & Stack
- Terraform, AWS CLI
- GitHub Actions
- S3 + DynamoDB for state
- AWS CDK (optional)

## Learning Goals
- Terraform state management
- CI/CD for infrastructure
- AWS service integration
- Security and compliance

## Build Milestones
1. **Week 1**: Terraform setup + AWS provider
2. **Week 2**: Core infrastructure (VPC, EC2)
3. **Week 3**: GitHub Actions workflow
4. **Week 4**: State management + locking
5. **Week 5**: Advanced patterns (modules, workspaces)
