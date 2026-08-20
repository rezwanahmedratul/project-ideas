# Kubernetes Policy Guardrail Engine

**Category:** DevOps  
**Date:** 2026-08-19  
**Difficulty:** Intermediate–Advanced  

## Overview
A self-hosted service that enforces **Policy-as-Code** on a Kubernetes cluster, blocking non-compliant workloads before they are admitted and continuously auditing running resources. Built around Kyverno (or OPA/Gatekeeper), it gives a homelab or small team a paved road: no privileged pods, no latest-tag images, mandatory resource limits, and required labels — all enforced automatically.

## Architecture / Structure
```
policy-engine/
├── policies/            # Kyverno Policy & ClusterPolicy YAML
│   ├── require-limits.yaml
│   ├── disallow-latest.yaml
│   ├── no-privileged.yaml
│   └── require-labels.yaml
├── admission/           # Webhook config + tests
├── audit/               # CronJob that reports violations
├── dashboards/          # Grafana JSON for violation metrics
├── deploy/              # Helm values / kustomize
└── README.md
```

## Workflow
1. Define policies as code in `policies/`.
2. Install Kyverno (Helm) and apply policies to the cluster.
3. Admission controller rejects violating `kubectl apply` in real time.
4. An audit CronJob scans existing resources and pushes violation counts to Prometheus.
5. Grafana dashboard shows compliance trend over time.

## Tools
- Kubernetes (k3s/kind for local)
- Kyverno or OPA Gatekeeper
- Helm / Kustomize
- Prometheus + Grafana
- GitHub Actions for policy CI (conftest validation)

## Learning Goals
- Understand Kubernetes admission control and webhooks.
- Write declarative policy-as-code.
- Wire policy violations into observability metrics.
- Practice GitOps-style policy promotion (dev → prod namespaces).

## Build Milestones
1. Stand up a local k3s cluster and install Kyverno.
2. Write 3 core policies (limits, no-latest, no-privileged) and verify rejection behavior.
3. Add a 4th policy (required labels) + exception allowlist.
4. Build the audit CronJob + Prometheus metrics.
5. Create a Grafana dashboard and a CI job that lints policies with `kyverno CLI`.
