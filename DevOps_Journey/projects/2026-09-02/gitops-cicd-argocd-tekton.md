# Project: GitOps CI/CD Pipeline with ArgoCD and Tekton

## Overview
Implement a complete GitOps workflow where ArgoCD manages Kubernetes deployments while Tekton handles CI/CD pipelines. This project demonstrates infrastructure-as-code principles and automated application delivery.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                      GitHub Repository                      │
│  ├── apps/ (application source code)                       │
│  ├── kubernetes/ (K8s manifests)                           │
│  ├── tekton/ (pipeline definitions)                        │
│  └── argocd/ (application configs)                         │
└─────────────────────────────────────────────────────────────┘
                            │
         ┌──────────────────┼──────────────────┐
         │                  │                  │
         ▼                  ▼                  ▼
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│    GitHub       │ │     Tekton      │ │     ArgoCD      │
│    Webhook      │ │     Pipeline    │ │    Application  │
│                 │ │                 │ │                 │
│ Trigger on push │ │  Build → Test  │ │ Sync to K8s     │
│                 │ │  → Image push  │ │                 │
│                 │ │  → Notify      │ │ Auto-heal drift │
└────────┬────────┘ └────────┬────────┘ └────────┬────────┘
         │                   │                   │
         └───────────────────┼───────────────────┘
                             │
                    ┌────────▼────────┐
                    │  ECR / Docker   │
                    │  Container Registry
                    └─────────────────┘
                             │
                    ┌────────▼────────┐
                    │  Kubernetes     │
                    │  (EKS/GKE/K3s)  │
                    └─────────────────┘
```

## Workflow
1. Developer pushes code to GitHub
2. GitHub webhook triggers Tekton pipeline
3. Tekton: Build Docker image → Run tests → Push to registry
4. Update Kubernetes manifests with new image tag
5. Commit updated manifests back to Git
6. ArgoCD detects manifest changes and syncs to cluster
7. Automated health checks and rollbacks on failure

## Tools
- Kubernetes (EKS/GKE/K3s)
- ArgoCD
- Tekton Pipelines
- GitHub Actions / webhooks
- Docker / kaniko
- Helm
- AWS ECR / GCP Artifact Registry

## Learning Goals
- GitOps principles and benefits
- Declarative CI/CD with Tekton
- ArgoCD application management
- Automated rollback strategies
- Infrastructure-as-code best practices

## Build Milestones
- [ ] Week 1: Set up Kubernetes cluster
- [ ] Week 2: Install and configure ArgoCD
- [ ] Week 3: Deploy basic app manually
- [ ] Week 4: Install Tekton and create build pipeline
- [ ] Week 5: Integrate GitHub webhooks
- [ ] Week 6: Connect Tekton to ArgoCD
- [ ] Week 7: Implement automated testing
- [ ] Week 8: Add rollback and health checks
