# NixOS Immutable Infrastructure Manager with Drift Detection

## Overview

Build an infrastructure management system that leverages NixOS declarative configuration with automated drift detection. The system continuously monitors the gap between declared (nixos/configuration.nix) and actual system state, providing remediation workflows for immutable infrastructure enforcement.

## Architecture

```
┌──────────────────────────────────────────────┐
│          NixOS Configuration Manager         │
│                                              │
│  ┌─────────────┐  ┌──────────────────────┐   │
│  │ Config Repo │  │ Drift Detection Agent │   │
│  │ (flake.nix) │  │ (cron + nixos-rebuild)│   │
│  └─────────────┘  └──────────────────────┘   │
│                                              │
│  ┌─────────────┐  ┌──────────────────────┐   │
│  │ Remediation │  │ Alerting System      │   │
│  │ Pipeline    │  │ (Telegram + Email)   │   │
│  └─────────────┘  └──────────────────────┘   │
└──────────────────────────────────────────────┘
           ↓
    ┌─────────────┐
    │ Target Hosts │
    │ (NixOS)     │
    └─────────────┘
```

## Workflow

1. **Declaration**: All infrastructure defined in Nix flakes with reproducible builds
2. **Audit Cycle**: Automated comparison between desired state (flake.lock) and current system
3. **Drift Report**: Generate structured reports showing divergences with severity classification
4. **Remediation**: Optional automated apply or manual review workflow
5. **Rollback**: One-command revert to previous generation using NixOS rollbacks

## Tools

- NixOS with flakes enabled
- nixos-anywhere for remote provisioning
- home-manager for user configurations
- Promtail/Grafana for drift visualization
- Cron or systemd timers for scheduled checks

## Learning Goals

- Deep dive into NixOS declarative configuration model
- Understand immutable infrastructure principles
- Learn flake development and dependency management
- Practice infrastructure drift detection strategies

## Build Milestones

1. **Week 1**: Set up NixOS VM with basic service definitions
2. **Week 2**: Create drift detection script comparing state
3. **Week 3**: Implement automated remediation with approval gates
4. **Week 4**: Add visualization dashboard for drift metrics
5. **Week 5**: Extend to multi-host fleet management
