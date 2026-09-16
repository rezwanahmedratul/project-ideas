# Project: Terraform AWS Infrastructure with CDK

## Overview
Build a production-grade AWS infrastructure using both Terraform and AWS CDK, implementing VPC networking, EKS cluster, RDS, S3 buckets, and IaC best practices including modules and workspaces.

## Architecture
```
AWS Account
├── VPC (Public + Private subnets)
│   ├── Public: NAT Gateway, Bastion
│   └── Private: EKS nodes, RDS, ElastiCache
├── EKS Cluster (managed)
│   ├── Control Plane
│   └── Node Groups (autoscaling)
├── RDS PostgreSQL (multi-AZ)
├── S3 Buckets (static site, artifacts)
├── Route 53 + ACM (TLS certificates)
└── CloudWatch + X-Ray (monitoring)
```

## Workflow
1. Define infrastructure as code in Terraform modules or CDK
2. Plan changes with `terraform plan` or CDK diff
3. Apply with CI/CD pipeline (GitHub Actions)
4. Track state remotely (S3 + DynamoDB locking)
5. Drift detection with periodic plan runs

## Tools & Tech Stack
- **Terraform** — Declarative IaC
- **AWS CDK** — Infrastructure as Code via TypeScript
- **Terraform CDK (cdktf)** — Bridge between Terraform and CDK
- **Terragrunt** — Wrapper for DRY Terraform
- **Atlantis** — PR-based Terraform workflows
- **Terraform Cloud/Enterprise** — State management
- **Checkov** — Policy-as-code security scanning

## Learning Goals
- Terraform state management and remote backends
- Module composition and versioning
- AWS CDK constructs and custom resources
- Multi-account strategy with Terraform workspaces
- Security scanning in CI pipelines
- Cost estimation and tagging strategies

## Build Milestones
1. [ ] Create reusable VPC module
2. [ ] Deploy EKS cluster with managed node groups
3. [ ] Set up RDS with automated backups
4. [ ] Implement OIDC for GitHub Actions → AWS IAM
5. [ ] Create CDK construct library for common patterns
6. [ ] Add Checkov scanning to CI pipeline
7. [ ] Implement disaster recovery playbook

## Reference Links
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest)
- [AWS CDK Documentation](https://docs.aws.amazon.com/cdk/v2/guide/home.html)
- [cdktf GitHub](https://github.com/hashicorp/terraform-cdk)
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
