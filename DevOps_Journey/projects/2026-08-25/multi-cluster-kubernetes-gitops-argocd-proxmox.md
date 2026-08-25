# Project: Multi-Cluster Kubernetes GitOps with ArgoCD on Proxmox

## Overview
Build a production-grade multi-cluster Kubernetes deployment pipeline using ArgoCD for GitOps management across two clusters running on your Proxmox home lab. Implement automated sync policies, health monitoring, and application promotion workflows (dev → staging → prod).

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│                    GitHub Repo                       │
│  apps/argocd/apps.yaml (Application CRDs)           │
│  apps/argocd/argocd-cm.yaml (ConfigMap)             │
│  envs/dev/ | envs/staging/ | envs/prod/              │
│    └── helm-values.yaml per environment             │
│    └── kustomization.yaml                           │
├─────────────────────────────────────────────────────┤
│  Cluster A (Proxmox Node 1)                         │
│  └── ArgoCD + Apps (dev workload)                   │
│                                                         │
│  Cluster B (Proxmox Node 2)                         │
│  └── ArgoCD + Apps (staging + prod)                 │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Provision two Kubernetes clusters on Proxmox VMs using K3s or RKE2
2. Install ArgoCD on both clusters via Helm
3. Define Application resources in Git pointing to Helm charts in `envs/{env}/`
4. Configure sync policies: auto-sync for dev, manual approval for prod
5. Set up Health checks and Alerts (ArgoCD Webhooks → GitHub Actions)
6. Implement app-of-apps pattern for nested Application sets

## Tools
- **K3s** or **RKE2** on Proxmox VMs
- **ArgoCD** v2.9+
- **Helm** (charts as reusable templates)
- **GitHub Actions** (webhook triggers)
- **kubectl** with kubeconfig stored in ArgoCD Secrets

## Learning Goals
- Understand GitOps principles (declarative desired state)
- Master ArgoCD CRDs: Application, ApplicationSet, AppProject
- Learn multi-cluster management from a single control plane
- Practice RBAC policies across clusters
- Implement rollback strategies using Git history

## Build Milestones
1. [ ] Deploy K3s cluster #1 on Proxmox (1 node)
2. [ ] Deploy K3s cluster #2 on Proxmox (1 node)
3. [ ] Install ArgoCD on both clusters with Helm
4. [ ] Push GitOps repo to GitHub; connect ArgoCD to repo
5. [ ] Deploy a sample app (nginx) with environment-specific values
6. [ ] Configure auto-sync for dev; manual for prod
7. [ ] Set up notifications (Slack/Discord webhook) on sync failures
8. [ ] Add health dashboard and test a controlled rollout (blue-green)

## References
- https://argo-cd.readthedocs.io/en/stable/operator-manual/multicluster/
- https://github.com/fardeskhan/DevOps-Projects
