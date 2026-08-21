# Kubernetes GitOps Drift Monitor with Auto-Remediation

## Overview
A GitOps monitoring system that detects configuration drift between desired state (in Git) and actual cluster state, then automatically proposes or applies fixes via pull requests.

## Architecture
```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   Git Repo   │────▶│  Argo CD     │────▶│  K8s Cluster │
│  (Desired)   │     │  (Sync Check)│     │  (Actual)    │
└─────────────┘     └──────┬───────┘     └──────┬──────┘
                            │                    │
                            ▼                    ▼
                     ┌──────────────┐     ┌─────────────┐
                     │  Drift       │◀────│  kubectl     │
                     │  Detector    │     │  get diffs   │
                     └──────┬───────┘     └─────────────┘
                            │
                            ▼
                     ┌──────────────┐
                     │  PR          │
                     │  Generator   │
                     └──────────────┘
```

## Workflow
1. Cron job runs every 5 minutes on control plane
2. Compares Git manifests with `kubectl diff` output
3. Flags resource drift (configmaps, deployments, CRDs)
4. Opens PR to sync desired state when drift detected
5. Optional: auto-apply for non-critical config changes

## Tools
- **Argo CD** or **Flux** for GitOps foundation
- **kubectl** for live cluster inspection
- **GitHub Actions** for PR generation
- **Python/bash** for drift calculation logic

## Learning Goals
- Deep understanding of GitOps principles
- Kubernetes resource reconciliation loops
- Declarative vs. imperative state management
- Automated testing of infrastructure changes

## Build Milestones
1. [ ] Basic drift detection script (kubectl diff + Git comparison)
2. [ ] Alerting dashboard with Grafana
3. [ ] Automatic PR generation for detected drift
4. [ ] Categorize drift severity (critical/config/performance)
5. [ ] Add auto-remediation for approved drift categories
6. [ ] Integrate with existing Argo CD/Flux setup
