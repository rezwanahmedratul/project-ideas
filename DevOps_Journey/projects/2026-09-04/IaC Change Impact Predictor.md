# IaC Change Impact Predictor

## Overview
A tool that analyzes Terraform/Ansible playbooks to predict the impact of infrastructure changes before execution, identifying potential downtime, cost changes, and dependency conflicts.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────────┐
│            IaC Change Impact Predictor                   │
├─────────────┬──────────────┬──────────────┬─────────────┤
│  Parser     │  Dependency  │  Impact      │  Report     │
│  Engine     │    Graph     │  Simulator   │  Generator  │
├─────────────┴──────────────┴──────────────┴─────────────┤
│              Terraform/Ansible Parser                     │
└─────────────────────────────────────────────────────────┘
```

## Workflow
1. Parser ingests IaC files and builds resource dependency graph
2. Impact simulator models proposed changes in isolation
3. Dependency analysis identifies cascading effects
4. Report generator produces risk assessment with mitigation suggestions
5. Integration with PR workflow for pre-merge validation

## Tools
- Python with terraform-lib/ansible-playbook-parser
- NetworkX for dependency graph analysis
- Git for version control integration
- GitHub Actions for PR integration
- Jinja2 for report templates

## Learning Goals
- Infrastructure as Code analysis
- Dependency graph construction
- Risk assessment methodologies
- CI/CD integration patterns

## Build Milestones
1. **M1**: Terraform plan parser with resource extraction
2. **M2**: Dependency graph construction
3. **M3**: Impact simulation engine
4. **M4**: Risk scoring and categorization
5. **M5**: Ansible playbook analysis support
6. **M6**: GitHub PR integration with automated comments
