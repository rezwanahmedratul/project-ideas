# Kubernetes Multi-Cluster GitOps with ArgoCD and Spoke/Hub Architecture

## Overview

Build a production-grade multi-cluster Kubernetes management system using ArgoCD in a hub-and-spoke topology. This project implements GitOps principles across multiple clusters, enabling centralized control with decentralized execution — a pattern essential for enterprises managing diverse environments.

## Architecture

```
┌─────────────────────────────────────────┐
│         Hub Cluster (ArgoCD)            │
│  ┌─────────────┐  ┌──────────────────┐  │
│  │ App of Apps │  │ Repo Server      │  │
│  │ Application │  │ (Git sources)    │  │
│  └─────────────┘  └──────────────────┘  │
└─────────────────────────────────────────┘
           ↓         ↓         ↓
    ┌──────────┐ ┌──────────┐ ┌──────────┐
    │ Spoke 1  │ │ Spoke 2  │ │ Spoke 3  │
    │ (Dev)    │ │ (Staging)│ │ (Prod)   │
    └──────────┘ └──────────┘ └──────────┘
```

## Workflow

1. **Configuration Repository Structure**: Organize Git repositories with environment-specific Kustomize overlays or Helm charts
2. **App of Apps Pattern**: Deploy a root Application that references child Applications per cluster/environment
3. **Sync Wave Management**: Control deployment ordering across dependencies
4. **Rollback Automation**: Implement automatic rollback on health degradation detection
5. **Notification Integration**: Configure Slack/email alerts for sync status changes

## Tools

- ArgoCD v2.x with ApplicationSet
- kustomize for environment overlays
- Helm for chart templating
- GitHub Actions for CI validation
- kubectl and argocd CLI

## Learning Goals

- Master GitOps principles beyond single-cluster deployments
- Understand ApplicationSet parameters for dynamic resource generation
- Learn multi-cluster RBAC and security isolation patterns
- Practice infrastructure as code with Git-only deployments

## Build Milestones

1. **Week 1**: Single-cluster ArgoCD installation with basic apps
2. **Week 2**: Implement App of Apps pattern with 3 environments
3. **Week 3**: Add Prometheus monitoring and alerting integration
4. **Week 4**: Implement automated rollback and drift detection
5. **Week 5**: Create custom notification webhooks and dashboards
