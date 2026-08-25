# Project: Secure Container Registry with Notary and Supply Chain Integrity

## Overview
Deploy a private Docker container registry (Harbor or Docker Registry) with TLS, authentication, vulnerability scanning, and image signing using Docker Content Trust (DCT). Integrate with CI/CD to enforce signed images only, creating a complete supply chain security pipeline.

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│  CI/CD Pipeline (GitHub Actions)                    │
│  ├── Build image                                   │
│  ├── Sign image (docker trust sign)                 │
│  ├── Push to registry                               │
│  └── Deploy (requires signature verification)       │
├─────────────────────────────────────────────────────┤
│  Harbor Registry (self-hosted)                      │
│  ├── Projects / repos                              │
│  ├── Robot accounts (service principal auth)        │
│  ├── Vulnerability scanner (Trivy integrated)       │
│  ├── Webhook → external system                     │
│  └── Replication → DR site                         │
├─────────────────────────────────────────────────────┤
│  Infrastructure                                    │
│  ├── Nginx reverse proxy (TLS termination)         │
│  ├── Harbor DB (PostgreSQL)                        │
│  └── Redis (session cache)                          │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Deploy Harbor registry via Helm chart on Kubernetes
2. Generate self-signed TLS cert (or use Let's Encrypt) for HTTPS access
3. Create robot account for CI/CD push/pull operations
4. Enable Docker Content Trust on the CI runner
5. Sign built images during pipeline; push to Harbor
6. In Kubernetes, configure image pull policy to verify signatures
7. Enable Trivy vulnerability scanner; block pushes on critical CVEs
8. Set up replication to a disaster-recovery Harbor instance

## Tools
- **Harbor** (enterprise container registry)
- **Helm** (deployment)
- **Docker Content Trust** (image signing)
- **Notary** (signature verification backend)
- **Trivy** (vulnerability scanning)
- **Nginx Ingress Controller** (TLS termination)
- **GitHub Actions** (CI/CD integration)

## Learning Goals
- Container registry architecture and components
- TLS/certificate management for internal services
- Docker Content Trust: keys, signatures, and delegation
- Image signing workflow in CI/CD pipelines
- Vulnerability scanning integration with build gates
- Supply chain security best practices (SLSA framework awareness)

## Build Milestones
1. [ ] Deploy Harbor on minikube via Helm; expose via NodePort
2. [ ] Configure TLS with self-signed certs; test HTTPS access
3. [ ] Create robot account for CI; verify push/pull works
4. [ ] Enable Docker Content Trust locally; generate root and repository keys
5. [ ] Sign and push an image from CI pipeline
6. [ ] Configure Kubernetes to verify image signatures on pull
7. [ ] Enable Trivy scan; set tag-as-vulnerable on critical findings
8. [ ] Set up Harbor replication to secondary cluster

## References
- https://goharbor.io/docs/
- https://docs.docker.com/engine/security/trust/
