# Project: Infrastructure Drift Detection and Remediation

## Overview
Develop a continuous monitoring system that detects when live infrastructure diverges from declared state (Terraform/Ansible) and automatically remediates drift.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────────────┐
│              Drift Detection System                          │
│  ┌─────────────┐  ┌─────────────┐  ┌──────────────────┐   │
│  │ State       │  │ Drift       │  │ Remediation     │   │
│  │ Comparator  │  │ Detector    │  │ Engine          │   │
│  └─────────────┘  └─────────────┘  └──────────────────┘   │
│                                                           │
│  ┌─────────────────────────────────────────────────────┐  │
│  │           Alert & Compliance Dashboard               │  │
│  │  · Real-time drift map · Compliance scoring          │  │
│  └─────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

## Workflow
1. **Snapshot**: Capture current infrastructure state
2. **Compare**: Diff against desired state definition
3. **Classify**: Categorize drift severity
4. **Alert**: Notify team of significant drift
5. **Remediate**: Automatically fix safe drifts
6. **Report**: Generate compliance report

## Tools
- Terraform state parsing
- Python for comparison logic
- AWS/GCP/Azure SDKs
- PostgreSQL for history
- Grafana for visualization

## Learning Goals
- Infrastructure as Code principles
- State management
- Configuration drift patterns
- Automated remediation

## Build Milestones
1. Week 1: State snapshot system
2. Week 2: Comparison engine
3. Week 3: Drift classification
4. Week 4: Alerting integration
5. Week 5: Auto-remediation
6. Week 6: Dashboard and reporting
