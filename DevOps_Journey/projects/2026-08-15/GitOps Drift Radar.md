# GitOps Drift Radar

## Overview
A continuous compliance scanner that detects configuration drift in Kubernetes clusters managed by ArgoCD/Flux. It compares live cluster state against the desired Git state and surfaces differences in real-time dashboards.

## Architecture
```
┌─────────────┐     ┌──────────────┐     ┌──────────────┐
│  ArgoCD/Flux│────▶│ Drift Scanner│────▶│   Alerting   │
│  (Git Repo) │     │  (Python/Rust)│     │  (PagerDuty, │
└─────────────┘     └──────────────┘     │   Slack)     │
                                         └──────────────┘
                                               │
                                         ┌──────────────┐
                                         │  Grafana /   │
                                         │  Web Dashboard│
                                         └──────────────┘
```

## Workflow
1. **Scan**: Periodically query cluster resources and compare with Git manifest
2. **Detect**: Identify additions, deletions, or modifications not in source of truth
3. **Alert**: Notify via Slack/PagerDuty with diff details
4. **Dashboard**: Visualize drift trends over time
5. **Auto-reconcile**: Option to auto-remediate specific drift types

## Tools
- Kubernetes, ArgoCD, Flux
- Python or Rust for scanner
- Prometheus + Grafana for visualization
- Git (GitHub/GitLab) for state storage
- Slack/PagerDuty for alerts

## Learning Goals
- Understand GitOps principles and drift detection
- Learn Kubernetes API and resource management
- Build real-time monitoring and alerting systems
- Practice infrastructure-as-code practices

## Build Milestones
1. **M1**: Basic drift detection script comparing kubectl diff with Git
2. **M2**: Add periodic scanning with configurable intervals
3. **M3**: Integrate with alerting systems (Slack, email)
4. **M4**: Build Grafana dashboard with drift metrics
5. **M5**: Add auto-remediation for specific drift types
6. **M6**: Package as a Helm chart for easy deployment
