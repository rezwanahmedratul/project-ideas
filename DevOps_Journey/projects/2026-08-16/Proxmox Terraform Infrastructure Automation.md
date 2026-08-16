# Proxmox Terraform Infrastructure Automation

## Overview
Create a complete Terraform provider workflow to provision and manage virtual machines on Proxmox VE. Includes networking, storage pools, and snapshot management via code.

## Architecture
```
Terraform Config (.tf files)
    ↓
Proxmox Terraform Provider
    ↓
Proxmox API (REST)
    ↓
QEMU/KVM Virtual Machines
    ↓
Ceph/LVM Storage
```

## Workflow
1. Install Terraform and Proxmox provider
2. Define VM templates in HCL
3. Create VMS programmatically with defined specs
4. Set up network bridges and firewall rules
5. Configure backup schedules via Proxmox API
6. Implement destroy/recreate workflows

## Tools
- Proxmox VE (7.x or 8.x)
- Terraform
- proxmoxer (Python library)
- Ansible for post-provisioning config
- Packer for VM template creation

## Learning Goals
- Infrastructure as Code principles
- Proxmox API internals
- Template-based VM provisioning
- Automated backup strategies

## Build Milestones
- [ ] Install Terraform + Proxmox provider
- [ ] Write basic VM provisioning config
- [ ] Add network bridge configuration
- [ ] Implement snapshot workflows
- [ ] Create destroy/recreate pipeline
- [ ] Add monitoring and alerting

## References
- https://registry.terraform.io/providers/Terraform-providers/proxmox/latest/docs
- https://boubekeur.net/Guides/terraform-proxmox-guide.html
- https://pve.proxmox.com/wiki/REST_API
