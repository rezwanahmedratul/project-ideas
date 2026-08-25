# Project: GitHub Actions CI/CD Pipeline for Go Microservices

## Overview
Build a fully automated CI/CD pipeline using GitHub Actions for a Go microservices project. Each service has its own pipeline with build, test, security scan, container image creation, and deployment to a Kubernetes cluster. Include matrix builds and artifact caching.

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│  GitHub Repository                                  │
│  ├── .github/workflows/                             │
│  │   ├── ci.yml          (lint + test on PR)       │
│  │   ├── cd-dev.yml      (build + deploy to dev)   │
│  │   └── cd-prod.yml     (manual approval → deploy)│
│  ├── services/                                      │
│  │   ├── user-service/    (main.go, Dockerfile)    │
│  │   ├── order-service/   (main.go, Dockerfile)    │
│  │   └── notification-svc/                            │
│  └── deploy/k8s/   (Helm charts or Kustomize)      │
├─────────────────────────────────────────────────────┤
│  Registry: ghcr.io / quay.io                        │
│  Target: Kubernetes (EKS or self-hosted)            │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Create monorepo with 3 Go microservices, each with a Dockerfile
2. Write `.github/workflows/ci.yml`: golangci-lint, unit tests, build verification
3. Write `.github/workflows/cd-dev.yml`: build image → push to registry → deploy to dev cluster
4. Add deployment gate: require manual approval for prod (`workflow_dispatch`)
5. Use matrix strategy to run CI tests in parallel across Go versions
6. Cache Go module downloads with `actions/cache`
7. Integrate Trivy for container vulnerability scanning post-build
8. Use `kubectl` or `helm` action for Kubernetes deployment

## Tools
- **GitHub Actions** (workflows, runners, matrix, secrets)
- **golangci-lint** (static analysis)
- **Trivy** (container image scanning)
- **ko** or **docker buildx** (container image builds)
- **Helm** or **kubectl** (deployment manifests)
- **GitHub Environments** (protection rules, required reviewers)

## Learning Goals
- GitHub Actions workflow syntax and contextual expressions
- Matrix builds for cross-version compatibility testing
- Artifact caching (Go modules, npm packages)
- Container image builds with buildx and multi-platform support
- Kubernetes deployments from GitHub Actions
- Manual approval gates and branch protection integration

## Build Milestones
1. [ ] Initialize monorepo; create 3 Go service directories with Dockerfiles
2. [ ] Write CI workflow: lint + test with matrix (Go 1.21, 1.22, 1.23)
3. [ ] Add `actions/cache` for Go module cache
4. [ ] Write dev CD workflow: build → push → deploy to minikube
5. [ ] Add Trivy scan step with fail-on-high-severity
6. [ ] Set up GitHub Environment "prod" with required reviewers
7. [ ] Write prod CD workflow with manual approval trigger
8. [ ] Document pipeline flow and add a README diagram

## References
- https://docs.github.com/en/actions
- https://github.com/fardeskhan/DevOps-Projects
