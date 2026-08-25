# Project: Ansible Automation Platform for Server Configuration Management

## Overview
Build a complete configuration management system using Ansible to provision, configure, and maintain a fleet of Linux servers. Include inventory management, role-based playbooks, dynamic inventories, and integration with a CMDB for tracking server state.

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│  Ansible Controller Node                             │
│  ├── group_vars/                                    │
│  │   ├── webservers.yml                             │
│  │   └── dbservers.yml                              │
│  ├── roles/                                         │
│  │   ├── common/     (packages, users, sshd)        │
│  │   ├── nginx/      (install, config, enable)      │
│  │   ├── postgresql/ (install, backup config)       │
│  │   └── monitoring/ (node_exporter, alerting)      │
│  ├── playbooks/                                     │
│  │   ├── deploy-web.yml                             │
│  │   └── patch-all.yml                              │
│  ├── inventory/                                     │
│  │   ├── hosts.ini                                  │
│  │   └── ec2.py (dynamic inventory script)          │
│  └── ansible.cfg                                    │
├─────────────────────────────────────────────────────┤
│  Target Nodes (VMs / containers)                     │
│  ├── Web Server 1 (Ubuntu 22.04)                    │
│  ├── Web Server 2 (Ubuntu 22.04)                    │
│  └── DB Server 1 (Debian 12)                        │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Set up Ansible controller on a fresh Ubuntu VM
2. Create static inventory file with host groups
3. Write `common` role: install essential packages, configure SSH keys, enable firewall
4. Write `nginx` role: install, configure virtual hosts, SSL certs via Let's Encrypt
5. Write `postgresql` role: install, configure auth, create databases, schedule backups
6. Create playbook `deploy-web.yml` that applies common + nginx to webservers group
7. Add dynamic inventory script querying Proxmox or AWS EC2 API
8. Implement Ansible Vault for secrets (database passwords, API keys)
9. Set up cron job for weekly patching playbook (`patch-all.yml`)

## Tools
- **Ansible** (core + collections: community.general, ansible.posix)
- **Proxmox VE** (for target VM provisioning)
- **AWX** (optional: web UI and job scheduling)
- **Ansible Vault** (encrypted variables)
- **Inventorystats** plugin for tracking managed nodes

## Learning Goals
- Ansible roles, playbooks, and handlers
- Variable precedence (group_vars vs host_vars vs extra vars)
- Dynamic inventory with Python scripts
- Ansible Vault for secret management
- idempotent playbooks and diff mode
- Tower/AWX job templates and schedules

## Build Milestones
1. [ ] Install Ansible on controller VM; test connectivity to targets
2. [ ] Write and apply `common` role across all nodes
3. [ ] Write `nginx` role; deploy HTTPS site with certbot
4. [ ] Write `postgresql` role; verify db creation and backups
5. [ ] Create vault-encrypted `group_vars/webservers.yml`
6. [ ] Add dynamic Proxmox inventory script
7. [ ] Schedule weekly `patch-all.yml` via cron
8. [ ] Deploy AWX on a VM and import inventories/playbooks

## References
- https://docs.ansible.com/ansible/latest/user_guide/index.html
- https://github.com/fardeskhan/DevOps-Projects
