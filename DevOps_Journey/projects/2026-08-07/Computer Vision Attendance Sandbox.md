# Computer Vision Attendance Sandbox

**Category:** AI ML  
**Suggested Date:** 2026-08-07  
**Status:** Idea / Not Started

## Overview
A privacy-aware attendance prototype that detects presence from images without storing raw faces long-term.

## What It Will Do
- Solve a practical problem related to ai ml.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
Camera/input module extracts embeddings, stores hashed/rotated identifiers, dashboard shows attendance confidence and audit trails.

### Suggested Repository Structure
```text
computer-vision-attendance-sandbox/
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
OpenCV, PyTorch, FastAPI, PostgreSQL, Docker, optional ONNX Runtime

## Learning Goals
Learn CV pipelines, privacy tradeoffs, model serving, and ethical ML design.

## Build Milestones
- **MVP:** Core workflow runs locally with Docker Compose.
- **v1:** Add tests, CI, logs, and basic dashboard/API docs.
- **v2:** Deploy to a homelab or cloud VM/Kubernetes cluster.
- **Portfolio polish:** Add architecture diagram, screenshots, and a short demo video.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
