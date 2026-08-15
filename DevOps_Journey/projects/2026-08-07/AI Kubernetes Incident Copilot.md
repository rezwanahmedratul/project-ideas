# AI Kubernetes Incident Copilot

**Category:** Combined  
**Suggested Date:** 2026-08-07  
**Status:** Idea / Not Started

## Overview
A DevOps+AI assistant that explains Kubernetes incidents and suggests runbooks using cluster logs, events, and metrics.

## What It Will Do
- Solve a practical problem related to combined.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
Collectors gather kubectl events/logs/Prometheus metrics; RAG layer retrieves internal runbooks; assistant outputs probable cause, commands to inspect, and safe remediation steps.

### Suggested Repository Structure
```text
ai-kubernetes-incident-copilot/
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
Kubernetes, Prometheus, Loki, FastAPI, Qdrant, local LLM/Ollama, Grafana, Telegram alerts

## Learning Goals
Combine observability, RAG, Kubernetes troubleshooting, and AI-assisted SRE.

## Build Milestones
- **MVP:** Core workflow runs locally with Docker Compose.
- **v1:** Add tests, CI, logs, and basic dashboard/API docs.
- **v2:** Deploy to a homelab or cloud VM/Kubernetes cluster.
- **Portfolio polish:** Add architecture diagram, screenshots, and a short demo video.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
