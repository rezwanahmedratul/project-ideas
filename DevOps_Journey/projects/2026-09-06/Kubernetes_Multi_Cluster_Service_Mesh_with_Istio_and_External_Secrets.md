# Kubernetes Multi-Cluster Service Mesh with Istio and External Secrets

## Overview
Build a production-ready service mesh across multiple Kubernetes clusters using Istio, with secrets managed by External Secrets Operator syncing from HashiCorp Vault or AWS Secrets Manager.

## Architecture
```
┌─────────────────┐     ┌─────────────────┐
│  Cluster A      │◄───►│  Cluster B      │
│  (East)         │     │  (West)         │
│                 │     │                 │
│  Istio Control  │     │  Istio Control  │
│  Pilot + Citadel│     │  Pilot + Citadel│
│                 │     │                 │
│  Workloads ─────┼─────┼─── Workloads    │
└─────────────────┘     └─────────────────┘
          │                       │
          └───────────┬───────────┘
                      │
              ┌───────▼────────┐
              │  External      │
              │  Secrets       │
              │  (Vault/AWS)   │
              └────────────────┘
```

## Workflow
1. Deploy Istio control plane in each cluster
2. Configure cross-cluster certificate authority via Citadel
3. Install External Secrets Operator in all clusters
4. Create SecretStore resources pointing to Vault/AWS
5. Deploy workloads with sidecar injection
6. Configure mTLS policies for east-west traffic

## Tools
- Kubernetes 1.28+
- Istio 1.20+
- External Secrets Operator
- HashiCorp Vault or AWS SM
- argocd for GitOps management

## Learning Goals
- Multi-cluster service mesh architecture
- Distributed certificate management
- Secrets management at scale
- Cross-cluster networking patterns

## Build Milestones
- [ ] Week 1: Single cluster Istio + mTLS
- [ ] Week 2: Second cluster deployment
- [ ] Week 3: Cross-cluster communication
- [ ] Week 4: External Secrets integration
- [ ] Week 5: Traffic management policies
- [ ] Week 6: Observability and monitoring
