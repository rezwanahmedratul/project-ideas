# Kubernetes GitOps Sync Validator

## Overview
Build a tool that monitors a Kubernetes cluster and validates that actual state matches the desired GitOps configuration. Detects drift between live cluster state and the source of truth in your Git repository, providing alerts and automated fix suggestions.

## Architecture
```
Git Repository (ArgoCD/Flux) 
    ↓
Cluster State Monitor (Polling/Webhook)
    ↓
Diff Engine (Kustomize/Custom)
    ↓
Drift Detector
    ↓
Alert System (Slack/Email) + Auto-Fix Suggester
```

## Workflow
1. Deploy a sample app on a local K8s cluster (minikube/kind)
2. Create ArgoCD application with Git source
3. Intentionally drift the cluster state (change replica count, config)
4. Build validator that detects mismatches using `kubectl diff` or custom policy engine
5. Add alerting to notification channel
6. Implement suggested remediation manifest generation

## Tools
- Kubernetes (kind/minikube)
- ArgoCD or Flux CD
- Helm/Kustomize
- Python or Go for custom controller
- Prometheus + Grafana for monitoring

## Learning Goals
- Deep understanding of GitOps principles
- Kubernetes API server interactions
- Declarative vs imperative state reconciliation
- Policy enforcement at scale

## Build Milestones
- [ ] Deploy K8s cluster with sample app
- [ ] Configure ArgoCD sync
- [ ] Implement drift detection script
- [ ] Add Slack webhook notifications
- [ ] Generate auto-fix manifests
- [ ] Dashboard with drift visualization

## References
- https://argoproj.github.io/cd/
- https://fluxcd.io/
- https://kubernetes.io/docs/concepts/overview/working-with-objects/kubectl/#diff
