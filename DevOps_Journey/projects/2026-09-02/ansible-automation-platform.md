# Project: Ansible Automation Platform with Inventory Management

## Overview
Create a comprehensive Ansible automation platform managing heterogeneous infrastructure — from cloud VMs to network devices. Learn dynamic inventory, role development, and secrets management.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                  Control Node (Ansible)                     │
│  ├── ansible.cfg                                           │
│  ├── inventory/                                            │
│  │   ├── aws_ec2.yaml  (dynamic)                          │
│  │   ├── vmware.yaml   (dynamic)                          │
│  │   └── hosts.ini     (static)                           │
│  ├── roles/                                                │
│  │   ├── nginx/     (web server)                          │
│  │   ├── postgres/  (database)                            │
│  │   ├── docker/    (container runtime)                   │
│  │   └── monitoring/ (prometheus stack)                   │
│  ├── playbooks/                                            │
│  │   ├── deploy.yml                                  │
│  │   ├── patch.yml                                   │
│  │   └── rollback.yml                                │
│  └── vault/ (encrypted secrets)                          │
└─────────────────────────────────────────────────────────────┘
                            │
         ┌──────────────────┼──────────────────┐
         ▼                  ▼                  ▼
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│    AWS EC2      │ │  VMware VMs     │ │  PhysicalServers│
│  - Web Servers  │ │  - Dev Envs     │ │  - Legacy Apps  │
│  - App Servers  │ │  - Staging      │ │  - Network Dev  │
└─────────────────┘ └─────────────────┘ └─────────────────┘
```

## Workflow
1. Set up control node with Ansible
2. Configure dynamic inventories (AWS EC2, VMware)
3. Develop reusable roles for common services
4. Create playbooks for deployment scenarios
5. Implement Ansible Vault for secrets
6. Test with Molecule
7. Deploy to target infrastructure

## Tools
- Ansible
- AWX / Ansible Tower (optional)
- AWS EC2 Dynamic Inventory
- VMware vCenter Inventory
- Ansible Vault
- Molecule (testing)

## Learning Goals
- Dynamic inventory management
- Role-based playbook organization
- Secrets encryption with Vault
- Testing automation with Molecule
- Multi-platform configuration management

## Build Milestones
- [ ] Week 1: Control node setup and basics
- [ ] Week 2: Static inventory and first playbooks
- [ ] Week 3: Develop nginx role
- [ ] Week 4: Develop postgres role
- [ ] Week 5: AWS dynamic inventory
- [ ] Week 6: VMware inventory integration
- [ ] Week 7: Ansible Vault implementation
- [ ] Week 8: Molecule testing and documentation
