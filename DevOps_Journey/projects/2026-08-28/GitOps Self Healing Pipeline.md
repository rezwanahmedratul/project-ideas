# DevOps: GitOps Self-Healing Pipeline

## Overview
Create a GitOps pipeline that doesn't just declaratively manage infrastructure but continuously verifies desired state and self-heals when drift is detected — automatically reconciling configuration back to the Git source of truth.

## Architecture
```
Git Repository → Argo CD / Flux
                     ├── State Verifier (continuous reconciliation)
                     ├── Drift Detector (compare live vs desired)
                     └── Auto-Reconciler (apply fixes, notify team)
```

## Workflow
1. Git repo declares desired state for infrastructure and apps
2. Argo CD/Flux syncs to cluster
3. Continuous controller checks for drift every 5 minutes
4. On drift detection, auto-reconciles non-critical changes
5. Critical drift triggers approval workflow for human review

## Tools
Argo CD, Flux CD, Helm, Kubernetes, Python, GitHub Actions

## Learning Goals
- GitOps principles and tooling
- Continuous reconciliation patterns
- Drift detection and remediation
- Approval workflows for production safety

## Build Milestones
1. Deploy Argo CD with a sample app manifest
2. Build drift detection controller with periodic reconciliation
3. Categorize drift as critical vs. non-critical
4. Implement auto-reconcile for non-critical changes
5. Add approval gate with Slack notification for critical drift
