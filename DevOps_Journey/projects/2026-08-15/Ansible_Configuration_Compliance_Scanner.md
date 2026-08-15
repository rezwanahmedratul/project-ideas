# Ansible Configuration Compliance Scanner

**Category:** DevOps
**Suggested Date:** 2026-08-15
**Status:** Idea / Not Started

## Overview
A scanner that audits infrastructure configurations across servers and cloud resources against policy-as-code baselines, reporting drift and remediation actions automatically.

## What It Will Do
- Solve a practical problem related to devops.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
compliance-scanner/
├── README.md
├── policies/
│   ├── baseline.yaml
│   └── custom/
├── playbooks/
│   ├── scan.yml
│   └── remediate.yml
├── inventory/
├── reports/
└── .github/workflows/

## How It Will Work
1. Define the core use case and minimal working workflow.
2. Build the API/automation pipeline first.
3. Add persistence, observability, and error handling.
4. Containerize the application and add CI.
5. Write documentation and create a demo scenario.

## Tools / Tech Stack
Ansible, Open Policy Agent, YAML policies, Docker Compose, GitHub Actions, Prometheus Blackbox Exporter

## Learning Goals
Learn policy-as-code, Ansible roles/galaxy patterns, compliance auditing, automated remediation playbooks, and audit logging.

## Build Milestones
- **MVP:** Single-node scan against a baseline YAML policy.
- **v1:** Multi-node inventory with pass/fail reports.
- **v2:** Automated remediation for common violations.
- **Portfolio polish:** Architecture diagram, sample policy library, demo video.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
