# Proxmox Terraform Infrastructure Automation

## Overview
Full infrastructure-as-code lifecycle for Proxmox VMs and containers using Terraform, enabling declarative provisioning, version-controlled infrastructure, and automated backups.

## Architecture
```
┌─────────────────┐     ┌─────────────────┐     ┌──────────────┐
│  Terraform      │────▶│  Proxmox VE     │────▶│  VMs/CTs     │
│  Config (HCL)   │     │  API            │     │  (Running)   │
└─────────────────┘     └────────┬────────┘     └──────────────┘
                                 │
                        ┌────────▼────────┐
                        │  Terraform      │
                        │  State & Plan   │
                        └─────────────────┘
```

## Workflow
1. Define VM/container specifications in HCL
2. Run `terraform plan` to preview changes
3. Apply changes with approval gate
4. Automate with CI/CD pipeline
5. Track state in remote backend (S3/Git)

## Tools
- **Proxmox VE** (virtualization platform)
- **Terraform Proxmox Provider** (`tambov/proxmox`)
- **GitHub Actions** or **GitLab CI** for automation
- **Vault** for credential management

## Learning Goals
- Infrastructure as Code fundamentals
- Proxmox API and REST interface
- Terraform provider development concepts
- State management and locking

## Build Milestones
1. [ ] Set up Proxmox Terraform provider
2. [ ] Create single VM from template
3. [ ] Define variable-driven VM configurations
4. [ ] Add networking and storage pools
5. [ ] Implement backup schedule via Terraform
6. [ ] Create CI/CD pipeline for infra changes
7. [ ] Add monitoring with Prometheus exporter
