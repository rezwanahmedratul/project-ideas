# Project: GitOps Drift Detector with Auto-Remediation

**Category:** DevOps  
**Date:** 2026-08-20

---

## Overview

Build a GitOps drift detection system that continuously compares live infrastructure state against desired state defined in Git, identifies deviations, and optionally auto-remediates them. This tool is essential for maintaining infrastructure consistency in teams practicing GitOps.

---

## What It Does

- Polls Infrastructure-as-Code (Terraform, Pulumi, Crossplane) state from Git
- Queries live cloud resources via provider APIs
- Computes diff between desired and actual state
- Alerts on drift (Slack, email, GitHub Issues)
- Optionally creates PRs to remediate or apply fixes
- Tracks drift history and trends over time

---

## Architecture/Structure

```
gitops-drift-detector/
├── src/
│   ├── collector.py      # Query live infrastructure
│   ├── reconciler.py     # Compare desired vs actual
│   ├── notifier.py       # Alert delivery (Slack, email, Issues)
│   └── remediator.py     # Auto-fix drift (optional)
├── config/
│   ├── providers.yaml    # Cloud provider configs
│   └── alert-rules.yaml  # Drift severity thresholds
├── scripts/
│   ├── poll.sh           # Cron entrypoint
│   └── migrate_state.py  # State migration tools
├── tests/
│   ├── test_reconciler.py
│   └── fixtures/         # Sample terraform state
└── Dockerfile
```

---

## Workflow

1. **Cron trigger** runs every 15 minutes
2. **Collector** fetches live state from AWS/GCP/Azure APIs
3. **Reconciler** diffs against Git-tracked Terraform plans
4. **Notifier** posts drift report to Slack channel
5. **Remediator** (if enabled) creates PR with fix or applies directly
6. **Dashboard** shows drift metrics over time

---

## Tools/Tech Stack

| Component | Technology |
|-----------|------------|
| Language | Python 3.11+ |
| IaC Parsing | terraform-json, cdktf |
| Cloud APIs | boto3, google-cloud-* |
| Git Operations | PyGithub, GitPython |
| Notifications | Slack API, SMTP |
| Scheduling | cron or GitHub Actions |
| Container | Docker |

---

## Learning Goals

- Understand GitOps principles and drift detection patterns
- Learn Terraform state management and diffing
- Practice cloud provider API integration
- Build automated remediation workflows
- Implement alerting and notification systems

---

## Build Milestones

1. **Week 1:** Basic drift detection for AWS EC2 + S3
2. **Week 2:** Multi-cloud support (AWS + GCP)
3. **Week 3:** Slack/email notifications with drift summaries
4. **Week 4:** Auto-remediation via PR creation
5. **Week 5:** Historical drift tracking and dashboard
6. **Week 6:** Containerize and deploy as Kubernetes Operator

---

## Stretch Goals

- Support for Kubernetes Helm chart drift
- ML-based drift prediction (anomaly detection)
- Cost impact analysis of drifted resources
- Integration with ArgoCD/Flux CD
