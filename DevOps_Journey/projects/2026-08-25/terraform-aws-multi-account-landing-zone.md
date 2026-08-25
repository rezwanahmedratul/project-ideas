# Project: Terraform AWS Multi-Account Infrastructure Landing Zone

## Overview
Design and deploy an AWS Landing Zone using Terraform across multiple accounts (dev, staging, prod) with enforced security baseline, centralized logging, and shared network VPC peering. This simulates enterprise infrastructure-as-code best practices.

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│  AWS Organization (Management Account)               │
│  ├── CloudTrail (centralized logging)                │
│  ├── GuardDuty (security monitoring)                 │
│  └── SCPs (Service Control Policies)                │
├─────────────────────────────────────────────────────┤
│  Dev Account                                       │
│  └── VPC (public/private subnets)                   │
│      └── EC2 / ECS tasks                            │
│                                                         │
│  Staging Account                                   │
│  └── VPC + RDS (MySQL)                              │
│                                                         │
│  Prod Account                                      │
│  └── VPC + RDS (multi-AZ) + ELB                     │
│      └── ALB + ECS/Fargate                          │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Create AWS Organization with multiple accounts via AWS CLI
2. Write Terraform modules for VPC, security groups, IAM roles
3. Use workspaces or separate state files per account
4. Apply SCPs to restrict dangerous actions in non-prod accounts
5. Enable CloudTrail and CloudWatch Logs cross-account subscription
6. Deploy a sample service (e.g., Python Flask API) in each account
7. Set up S3 bucket versioning and encryption policies via Terraform

## Tools
- **Terraform** (Cloudflare provider for state locking + remote backend)
- **AWS CLI** v2
- **aws-org** module or AWS Control Tower
- **Checkov** or **tfsec** for policy-as-code scanning
- **GitLab CI / GitHub Actions** for pipeline validation

## Learning Goals
- Terraform workspaces vs. separate state files strategy
- AWS Organizations, SCPs, and policy enforcement
- Cross-account VPC peering / Transit Gateway concepts
- Security baseline automation (S3 encryption, no public subnets)
- Cost tagging strategy across environments

## Build Milestones
1. [ ] Write Terraform provider block with assumed-role for org account
2. [ ] Create 3 AWS accounts via Organization API (or use localstack)
3. [ ] Module: reusable VPC (public/private subnets, NAT Gateway)
4. [ ] Module: security groups with least-privilege ingress rules
5. [ ] Apply SCPs restricting IAM actions and resource deletion
6. [ ] Deploy sample microservice in each account
7. [ ] Enable centralized CloudTrail + GuardDuty
8. [ ] Add pre-commit hooks with tfsec scan on every push

## References
- https://docs.aws.amazon.com/landing-zone/latest/userguide/landing-zone.html
- https://www.clouddevopshub.com/blog/25-real-time-devops-projects-to-build-your-portfolio
