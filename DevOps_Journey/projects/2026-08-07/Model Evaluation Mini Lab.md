# Model Evaluation Mini Lab

**Category:** AI ML  
**Suggested Date:** 2026-08-07  
**Status:** Idea / Not Started

## Overview
A reproducible benchmark lab to compare small LLMs on coding, reasoning, and DevOps troubleshooting prompts.

## What It Will Do
- Solve a practical problem related to ai ml.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
Dataset of tasks is versioned; runner executes prompts against models; evaluator scores outputs with rubrics and stores metrics in dashboards.

### Suggested Repository Structure
```text
model-evaluation-mini-lab/
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
lm-eval-harness, Python, Hugging Face, Ollama/vLLM, W&B or MLflow, Pandas, Grafana

## Learning Goals
Learn evaluation methodology, benchmark design, experiment tracking, and model selection.

## Build Milestones
- **MVP:** Core workflow runs locally with Docker Compose.
- **v1:** Add tests, CI, logs, and basic dashboard/API docs.
- **v2:** Deploy to a homelab or cloud VM/Kubernetes cluster.
- **Portfolio polish:** Add architecture diagram, screenshots, and a short demo video.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
