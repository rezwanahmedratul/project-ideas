# GitOps Drift Radar

**Category:** DevOps  
**Suggested Date:** 2026-08-07  
**Status:** Idea / Not Started

## Overview
A dashboard that continuously compares live Kubernetes cluster state against Git desired state and highlights configuration drift before it becomes production risk.

## What It Will Do
- Solve a practical problem related to devops.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
Agents collect Kubernetes manifests from Git, query live cluster objects, normalize both into comparable JSON, run policy checks, and publish a drift score per namespace/service.

### Suggested Repository Structure
```text
gitops-drift-radar/
├── README.md
├── docs/
│   ├── architecture.md
│   └── setup.md
├── src/
│   ├── api/
│   ├── core/
│   └── workers/
├── infra/
│   ├── docker-compose.yml
│   └── terraform-or-k8s/
├── tests/
└── .github/workflows/
```

## How It Will Work
1. Define the core use case and minimal working workflow.
2. Build the API/automation pipeline first.
3. Add persistence, observability, and error handling.
4. Containerize the application and add CI.
5. Write documentation and create a demo scenario.

## Tools / Tech Stack
FluxCD or Argo CD, Kubernetes, Python/FastAPI, React, Open Policy Agent, Prometheus, Grafana, GitHub Actions

## Learning Goals
Learn GitOps, Kubernetes APIs, policy-as-code, observability, and incident-prevention workflows.

## Build Milestones
- **MVP:** Core workflow runs locally with Docker Compose.
- **v1:** Add tests, CI, logs, and basic dashboard/API docs.
- **v2:** Deploy to a homelab or cloud VM/Kubernetes cluster.
- **Portfolio polish:** Add architecture diagram, screenshots, and a short demo video.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
