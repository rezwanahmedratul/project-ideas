# Project: Proxmox VM Lifecycle Manager with Terraform

**Category:** DevOps  
**Date:** 2026-08-20

---

## Overview

Create a Terraform provider extension or wrapper that manages Proxmox Virtual Environment (PVE) virtual machines and containers with full lifecycle support — provisioning, snapshots, cloning, and decommissioning — integrated into your existing IaC pipelines.

---

## What It Does

- Define VMs/CTs in Terraform HCL configuration
- Provision VMs with custom templates and cloud-init
- Take and manage VM snapshots as part of resource lifecycle
- Clone VMs from templates for scaling
- Auto-decommission resources on `terraform destroy`
- Integrate with GitLab CI/CD for ephemeral environments

---

## Architecture/Structure

```
terraform-provider-proxmox-custom/
├── internal/
│   ├── client/         # Proxmox API client
│   ├── resource_vm.go  # VM resource
│   ├── resource_ct.go  # Container resource
│   └── snapshot.go     # Snapshot management
├── docs/
│   └── resources/      # Documentation
├── examples/
│   └── vm-basic/       # Example usage
├── main.go
└── Makefile
```

---

## Workflow

1. **Developer** writes Terraform config describing VMs
2. **CI Pipeline** runs `terraform plan` to preview changes
3. **Approval gate** triggers `terraform apply`
4. **Provider** calls Proxmox API to create VM/CT
5. **Post-provision** runs cloud-init and health checks
6. **Terraform state** tracks resources for future updates

---

## Tools/Tech Stack

| Component | Technology |
|-----------|------------|
| Provider SDK | Go (Terraform Plugin SDK v2) |
| API Client | proxmox-api-go or custom HTTP client |
| Testing | Terratest, Go testing |
| CI/CD | GitLab CI / GitHub Actions |
| Documentation | Terraform Registry format |

---

## Learning Goals

- Terraform provider development internals
- Proxmox VE API and authentication
- Go programming for infrastructure tooling
- CI/CD integration patterns
- Snapshot and clone management strategies

---

## Build Milestones

1. **Week 1:** Basic VM provisioning with QEMU/KVM
2. **Week 2:** LXC container support
3. **Week 3:** Snapshot resource type
4. **Week 4:** Clone from template functionality
5. **Week 5:** Destroy and cleanup logic
6. **Week 6:** Publish to Terraform Registry (private)

---

## Stretch Goals

- Support for Proxmox Cluster HA
- Resource dependency graph optimization
- Import existing VMs into Terraform state
- Webhook integration for VM events
