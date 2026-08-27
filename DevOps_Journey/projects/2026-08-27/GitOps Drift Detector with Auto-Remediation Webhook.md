# GitOps Drift Detector with Auto-Remediation Webhook

**Date:** 2026-08-27
**Category:** DevOps
**Tags:** gitops, drift-detection, argocd, flux, remediation

---

## Overview

Build a drift detection system that continuously compares live infrastructure state against Git-defined desired state. When unauthorized changes are detected, the system either auto-remediates or creates a ticket for review.

## Architecture

```
┌──────────────────────────────────────────────────────────┐
│                    Drift Detection System                 │
│                                                          │
│   ┌──────────┐    ┌──────────────┐    ┌───────────────┐  │
│   │  Timer /  │    │  State       │    │  Diff         │  │
│   │  Webhook  │───▶│  Collector   │───▶│  Engine       │  │
│   └──────────┘    └──────────────┘    └───────┬───────┘  │
│                                               │           │
│   ┌──────────┐    ┌──────────────┐            │           │
│   │  Ticket  │◄───│  Remediate   │◄───────────┘           │
│   │  Creator │    │  Engine      │                        │
│   └──────────┘    └──────────────┘                        │
└──────────────────────────────────────────────────────────┘
```

## Workflow

1. **Schedule:** Cron job runs every 5 minutes (or triggered by webhook on push)
2. **Collect:** Pull current state from infrastructure (Terraform state, K8s resources, cloud APIs)
3. **Compare:** Diff live state against Git-referenced desired state
4. **Classify:** Categorize drift as benign (expected) or malicious/unauthorized
5. **Act:** Auto-remediate low-risk changes; create issues for high-risk
6. **Notify:** Slack/Discord/webhook notification of detected drift

## Drift Types Detected

| Type | Example | Remediation |
|------|---------|-------------|
| Config drift | Security group changed manually | Auto-revert or alert |
| Resource drift | Instance type changed | Auto-revert |
| Orphaned resources | Untracked EC2 instance | Alert + optional cleanup |
| Missing resources | Desired resource not created | Trigger apply |
| Permission drift | IAM policy expanded | Alert immediately |

## Drift Classification

- **Low risk:** Within tolerance bands, expected variations
- **Medium risk:** Configuration changes, needs review
- **High risk:** Security-related, structural changes

## Tools

- **Python** with `boto3`/`google-cloud`/`azure-sdk`
- **Dockerfile** for containerized execution
- **GitHub Actions** or cron for scheduling
- **Slack webhook** for notifications
- **Jira/Linear API** for ticket creation

## Learning Goals

- Infrastructure state management concepts
- Difference engine design (JSON/YAML diff)
- Risk classification logic
- GitOps principles beyond CI/CD
- Secure credential handling

## Build Milestones

1. [ ] Define drift detection scope (start with AWS + K8s)
2. [ ] Implement state collector for Terraform-managed resources
3. [ ] Build diff engine comparing state vs Git manifests
4. [ ] Create drift classification ruleset
5. [ ] Implement auto-remediation for safe changes
6. [ ] Add ticket creation for risky drift
7. [ ] Containerize and deploy as scheduled task
8. [ ] Build dashboard showing drift trends

---
*Generated: 2026-08-27*
