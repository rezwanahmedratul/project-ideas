# Ansible Automation Platform with Inventory Management
**Date:** 2026-09-03  
**Category:** DevOps  
**Complexity:** Intermediate

---

## Overview

Build a complete Ansible automation platform with dynamic inventory management, role-based access control, execution pipelines, and comprehensive reporting for enterprise infrastructure automation.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│          Ansible Automation Platform                        │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  User Interface                                             │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  • Web Dashboard for playbook orchestration        │   │
│  │  • Role-based access control (RBAC)                │   │
│  │  • Execution history and audit trail               │   │
│  │  • Real-time job monitoring                        │   │
│  └─────────────────────────────────────────────────────┘   │
│                           │                                 │
│                    ┌──────▼──────┐                         │
│                    │  API        │                         │
│                    │  Gateway    │                         │
│                    │  (Ansible   │                         │
│                    │   Runner)   │                         │
│                    └──────┬──────┘                         │
│                           │                                │
│  ┌───────────────────────┼───────────────────────┐         │
│  │               │               │               │         │
│ ┌▼─────┐     ┌──▼────┐     ┌───▼────┐     ┌───▼────┐       │
│ │Dynamic│     │Roles  │     │Templates│     │Secrets │       │
│ │Inventory│    │Library│    │Management│    │Vault   │       │
│ └──┬───┘     └──┬────┘     └───┬────┘     └───┬────┘       │
│    │            │             │               │            │
│ ┌──▼───┐     ┌──▼────┐     ┌──▼────┐     ┌───▼────┐       │
│ │Cloud │     │Custom  │     │Jinja  │     │HashiCorp│      │
│ │APIs  │     │Modules │     │Engine │     │Vault   │      │
│ └──────┘     └───────┘     └───────┘     └────────┘       │
│                                                             │
│  Execution Layer                                            │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  • Tower/AWX for scheduling                          │   │
│  │  • Celery workers for parallel execution             │   │
│  │  • Container-based isolation                         │   │
│  │  • Retry and rollback support                        │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## Dynamic Inventory Sources

### Cloud Providers
```yaml
# inventory/aws.yml
plugin: aws_ec2
regions:
  - us-east-1
  - ap-south-1
filters:
  tag:Environment: production
  tag:Team: infrastructure
groups:
  webservers: "'nginx' in group_names"
  databases: "'postgresql' in group_names"
compose:
  ansible_host: public_ip_address
  environment: tags.Environment
```

### Custom Dynamic Inventory Script
```python
#!/usr/bin/env python3
"""
Dynamic inventory script for internal VM management
"""
import json
import requests
from datetime import datetime

def get_inventory():
    # Fetch from internal API
    resp = requests.get("http://homelab-api/hosts")
    hosts = resp.json()
    
    inventory = {
        "_meta": {
            "hostvars": {}
        },
        "all": {
            "children": ["webservers", "databases", "monitoring"]
        },
        "webservers": {"hosts": []},
        "databases": {"hosts": []},
        "monitoring": {"hosts": []}
    }
    
    for host in hosts:
        inventory["_meta"]["hostvars"][host["hostname"]] = {
            "ansible_host": host["ip"],
            "ansible_user": "deploy",
            "ansible_become": True,
            "custom_data": host.get("metadata", {})
        }
        
        for group in host.get("groups", []):
            if group in inventory:
                inventory[group]["hosts"].append(host["hostname"])
    
    return inventory

if __name__ == "__main__":
    print(json.dumps(get_inventory()))
```

## Role Library Structure

```
roles/
├── common/                    # Base configuration
│   ├── tasks/
│   │   └── main.yml
│   ├── handlers/
│   │   └── main.yml
│   ├── templates/
│   │   ├── resolv.conf.j2
│   │   └── limits.conf.j2
│   ├── vars/
│   │   └── main.yml
│   └── defaults/
│       └── main.yml
├── nginx/
│   ├── tasks/
│   │   ├── install.yml
│   │   ├── configure.yml
│   │   └── ssl.yml
│   └── templates/
│       └── nginx.conf.j2
├── postgresql/
│   └── ...
├── monitoring/
│   └── ...
└── kubernetes/
    └── ...
```

## Pipeline Integration

```yaml
# ansible-pipeline.yml
name: Infrastructure Pipeline
on:
  push:
    paths:
      - 'infrastructure/**'
  schedule:
    - cron: '0 2 * * *'  # Nightly config drift check

jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Validate Ansible syntax
        run: ansible-playbook --syntax-check playbooks/site.yml
      
  dry-run:
    needs: validate
    runs-on: ubuntu-latest
    steps:
      - name: Run Ansible in dry-run mode
        run: |
          ansible-playbook playbooks/site.yml --check --diff
  
  deploy:
    needs: dry-run
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    steps:
      - name: Deploy to production
        run: |
          ansible-playbook playbooks/site.yml \
            --inventory inventory/production.yml \
            --vault-password-file ~/.vault_pass
```

## Tools & Technologies

- **Ansible** core + **AWX/Tower** for management
- **Python** for custom modules and inventory
- **Docker** for isolated execution environments
- **GitHub Actions** for CI/CD integration
- **Prometheus** + **Grafana** for monitoring
- **Vault** for secrets management

## Learning Goals

- Master Ansible best practices and patterns
- Build dynamic inventory solutions
- Design reusable role libraries
- Implement GitOps workflows for infrastructure
- Manage secrets securely in automation

## Build Milestones

| Milestone | Description |
|-----------|-------------|
| M1 | Set up AWX/Tower with Ansible Runner |
| M2 | Create common role with base system config |
| M3 | Build dynamic inventory for cloud providers |
| M4 | Create nginx and PostgreSQL roles |
| M5 | Implement CI/CD pipeline integration |
| M6 | Add reporting, alerting, and drift detection |

## Reference Links

- [Ansible Documentation](https://docs.ansible.com/)
- [AWX Documentation](https://awx-project.readthedocs.io/)
- [Ansible Galaxy Roles](https://galaxy.ansible.com/)
- [Dynamic Inventory Guide](https://docs.ansible.com/ansible/latest/inventory_guide/intro_dynamic_inventory.html)
