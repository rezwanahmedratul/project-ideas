# Event Sourced Personal Finance Ledger

**Category:** Software Development  
**Suggested Date:** 2026-08-07  
**Status:** Idea / Not Started

## Overview
A clean software architecture project that stores every financial action as an immutable event and builds projections for budgets and analytics.

## What It Will Do
- Solve a practical problem related to software development.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
Commands append events to an event store; projectors build read models for accounts, categories, and monthly reports; API serves query views.

### Suggested Repository Structure
```text
event-sourced-personal-finance-ledger/
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
Java/Spring Boot or Go, PostgreSQL, Kafka/Redpanda optional, Docker, React dashboard

## Learning Goals
Learn event sourcing, CQRS, domain modeling, and reliable data systems.

## Build Milestones
- **MVP:** Core workflow runs locally with Docker Compose.
- **v1:** Add tests, CI, logs, and basic dashboard/API docs.
- **v2:** Deploy to a homelab or cloud VM/Kubernetes cluster.
- **Portfolio polish:** Add architecture diagram, screenshots, and a short demo video.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
