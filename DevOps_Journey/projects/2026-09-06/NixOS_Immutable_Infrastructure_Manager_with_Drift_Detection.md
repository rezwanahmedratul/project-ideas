# NixOS Immutable Infrastructure Manager with Drift Detection

## Overview
Create a NixOS-based infrastructure management tool that enforces immutability by comparing desired state (Nix expressions) against actual deployed state, alerting on any drift.

## Architecture
```
┌─────────────────────────────────────────┐
│         Drift Detection Engine          │
├─────────────────────────────────────────┤
│  Desired State (Nix)    Actual State   │
│  ┌─────────────┐        ┌──────────┐   │
│  │ flake.nix   │  →     │ nix-   │   │
│  │ outputs     │        │ store  │   │
│  └─────────────┘        └──────────┘   │
│         ↓ comparison                   │
│    ┌─────────────┐                     │
│    │ Drift Report│                     │
│    └─────────────┘                     │
└─────────────────────────────────────────┘
```

## Workflow
1. Define infrastructure as Nix flakes
2. Deploy to target nodes via NixOS remote builder
3. Scheduled job captures current system state
4. Diff desired vs actual configuration
5. Generate drift report with remediation suggestions
6. Auto-remediate non-critical drift

## Tools
- NixOS with flakes
- nixos-anywhere for provisioning
- custom drift detection script
- Prometheus + Grafana for dashboards
- Telegram webhook for alerts

## Learning Goals
- NixOS declarative configuration
- Infrastructure as code principles
- Drift detection algorithms
- Automated remediation patterns

## Build Milestones
- [ ] Week 1: NixOS base configuration
- [ ] Week 2: Flake structure design
- [ ] Week 3: Deployment automation
- [ ] Week 4: State capture mechanism
- [ ] Week 5: Drift detection logic
- [ ] Week 6: Alerting and remediation
