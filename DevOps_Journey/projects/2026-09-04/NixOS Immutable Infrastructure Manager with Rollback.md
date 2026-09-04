# NixOS Immutable Infrastructure Manager with Rollback

## Overview
A management layer on top of NixOS that treats infrastructure as immutable, automatically detects configuration drift, and provides instant rollback capabilities for production systems.

## Architecture/Structure
```
┌────────────────────────────────────────────────────┐
│            NixOS Infrastructure Manager            │
├──────────┬──────────┬──────────┬──────────────────┤
│ Drift    │ Rollback │ Audit    │ Compliance      │
│ Detector │ Engine   │ Logger   │ Checker         │
├──────────┼──────────┼──────────┼──────────────────┤
│          │ NixOS    │ Git      │ Policy Engine   │
│          │ Builder  │ History  │ (OpenPolicy)    │
└──────────┴──────────┴──────────┴──────────────────┘
```

## Workflow
1. Agent deployed to each NixOS node monitors system state
2. Compares current state against declared NixOS configuration
3. Alerts on drift (manual package installs, config file changes)
4. Auto-rollback to last known-good generation on critical drift
5. Audit trail stored in Git with timestamps and actor info

## Tools
- NixOS + Nixpkgs
- Dhall for configuration as code
- OpenPolicy Agent (OPA)
- Prometheus + Grafana for drift metrics
- GitHub Actions for CI/CD of configurations

## Learning Goals
- NixOS declarative configuration
- Immutable infrastructure principles
- Policy-as-code enforcement
- GitOps for infrastructure management

## Build Milestones
1. **M1**: Basic drift detection agent
2. **M2**: Rollback to previous NixOS generation
3. **M3**: Audit logging with Git integration
4. **M4**: OPA policy enforcement
5. **M5**: Multi-node dashboard with Grafana
6. **M6**: Automated compliance reporting
