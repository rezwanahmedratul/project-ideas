# Terraform Cost Guardrail Pipeline

**Category:** DevOps  
**Suggested Date:** 2026-08-07  
**Status:** Idea / Not Started

## Overview
A CI/CD pipeline that estimates cloud cost impact before infrastructure changes are merged.

## What It Will Do
- Solve a practical problem related to devops.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
Pull requests trigger Terraform plan, cost estimation, budget policy checks, and approval gates. Results are commented directly on the PR.

### Suggested Repository Structure
```text
terraform-cost-guardrail-pipeline/
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
Terraform, Infracost, GitHub Actions, OPA/Conftest, AWS Free Tier or LocalStack

## Learning Goals
Practice IaC governance, cost-aware DevOps, and policy-driven CI/CD.

## Build Milestones
- **MVP:** Core workflow runs locally with Docker Compose.
- **v1:** Add tests, CI, logs, and basic dashboard/API docs.
- **v2:** Deploy to a homelab or cloud VM/Kubernetes cluster.
- **Portfolio polish:** Add architecture diagram, screenshots, and a short demo video.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
