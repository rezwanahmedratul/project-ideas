# Daily DevOps / Software Development / AI-ML Project Ideas — 2026-08-07

Generated as a test run. Each project has its own Obsidian markdown file.

## DevOps: [[projects/2026-08-07/GitOps Drift Radar|GitOps Drift Radar]]

A dashboard that continuously compares live Kubernetes cluster state against Git desired state and highlights configuration drift before it becomes production risk.

**Tools:** FluxCD or Argo CD, Kubernetes, Python/FastAPI, React, Open Policy Agent, Prometheus, Grafana, GitHub Actions

## DevOps: [[projects/2026-08-07/Self Healing Homelab Controller|Self Healing Homelab Controller]]

An automation controller that detects common homelab failures and applies safe remediation playbooks with audit logs.

**Tools:** Ansible, Docker, systemd, Prometheus Blackbox Exporter, FastAPI, SQLite, Telegram bot alerts

## DevOps: [[projects/2026-08-07/Terraform Cost Guardrail Pipeline|Terraform Cost Guardrail Pipeline]]

A CI/CD pipeline that estimates cloud cost impact before infrastructure changes are merged.

**Tools:** Terraform, Infracost, GitHub Actions, OPA/Conftest, AWS Free Tier or LocalStack

## Software Development: [[projects/2026-08-07/Offline First Study Planner API|Offline First Study Planner API]]

A backend and web app for students that works offline-first and syncs notes, tasks, and schedules when connectivity returns.

**Tools:** FastAPI or Rust Axum, PostgreSQL, SQLite/PouchDB, React, service workers, Docker Compose

## Software Development: [[projects/2026-08-07/Plugin Based CLI Automation Framework|Plugin Based CLI Automation Framework]]

A developer CLI where users can install small plugins for Git, Docker, Kubernetes, logs, and project scaffolding.

**Tools:** Python Typer or Rust Clap, TOML/YAML manifests, uv/Nix flakes, pytest, GitHub Releases

## Software Development: [[projects/2026-08-07/Event Sourced Personal Finance Ledger|Event Sourced Personal Finance Ledger]]

A clean software architecture project that stores every financial action as an immutable event and builds projections for budgets and analytics.

**Tools:** Java/Spring Boot or Go, PostgreSQL, Kafka/Redpanda optional, Docker, React dashboard

## AI ML: [[projects/2026-08-07/Local RAG Research Notebook|Local RAG Research Notebook]]

A private research assistant that indexes PDFs, blog posts, and notes, then answers questions with citations from your own knowledge base.

**Tools:** Ollama or llama.cpp, Qdrant/Chroma, LangChain/LlamaIndex, FastAPI, Obsidian markdown, Docker

## AI ML: [[projects/2026-08-07/Model Evaluation Mini Lab|Model Evaluation Mini Lab]]

A reproducible benchmark lab to compare small LLMs on coding, reasoning, and DevOps troubleshooting prompts.

**Tools:** lm-eval-harness, Python, Hugging Face, Ollama/vLLM, W&B or MLflow, Pandas, Grafana

## AI ML: [[projects/2026-08-07/Computer Vision Attendance Sandbox|Computer Vision Attendance Sandbox]]

A privacy-aware attendance prototype that detects presence from images without storing raw faces long-term.

**Tools:** OpenCV, PyTorch, FastAPI, PostgreSQL, Docker, optional ONNX Runtime

## Combined: [[projects/2026-08-07/AI Kubernetes Incident Copilot|AI Kubernetes Incident Copilot]]

A DevOps+AI assistant that explains Kubernetes incidents and suggests runbooks using cluster logs, events, and metrics.

**Tools:** Kubernetes, Prometheus, Loki, FastAPI, Qdrant, local LLM/Ollama, Grafana, Telegram alerts

## Combined: [[projects/2026-08-07/MCP Server for Homelab Operations|MCP Server for Homelab Operations]]

An MCP server exposing safe homelab operations to AI agents, such as checking services, reading logs, restarting containers, and creating tickets.

**Tools:** Model Context Protocol, Python/TypeScript, Docker SDK, systemd, OPA, SQLite, NixOS modules

## Combined: [[projects/2026-08-07/AI Powered CI Failure Explainer|AI Powered CI Failure Explainer]]

A CI assistant that reads failed GitHub Actions logs, summarizes root causes, links likely files, and proposes fixes as PR comments.

**Tools:** GitHub Apps/API, FastAPI, Celery/Redis, tree-sitter, local/hosted LLM, Docker, PostgreSQL

