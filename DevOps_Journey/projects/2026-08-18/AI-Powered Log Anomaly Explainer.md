# AI-Powered Log Anomaly Explainer

**Category:** Combined  
**Date:** 2026-08-18  
**Difficulty:** Intermediate-Advanced

---

## Overview

A system that ingests Kubernetes/Prometheus/Loki logs, detects anomalies using ML, and uses a local LLM to explain *what* happened and *why* in plain language. Bridges observability (DevOps) with AI explanation (ML) — a self-hosted "Datadog AI" for homelabs.

## Architecture / Structure

```
log-explainer/
├── collect/
│   ├── loki.py            # Loki query client
│   └── k8s_events.py      # K8s API watcher
├── detect/
│   ├── window.py         # Sliding window aggregation
│   └── model.py          # IsolationForest / LSTM
├── explain/
│   ├── prompt.py         # RAG over runbooks
│   └── llm.py            # Ollama generate
├── notify/
│   └── telegram.py       # Rich alert cards
└── ui/
    └── dashboard.py      # Streamlit timeline
```

## Workflow

1. **Collect** logs/metrics from Loki + Prometheus every minute
2. **Detect** anomalies via ML (spike, drift, new error pattern)
3. **Correlate** with recent K8s events (pod restart, OOMKilled)
4. **Explain** → LLM generates root-cause hypothesis from context + runbook RAG
5. **Notify** → Telegram card: anomaly, likely cause, suggested fix, dashboard link
6. **Learn** → user feedback improves prompt/threshold

## Tools

- **Observability:** Loki, Prometheus, Grafana
- **ML:** Python, scikit-learn, PyTorch
- **LLM:** Ollama (qwen2.5:14b)
- **Orchestration:** Docker Compose, Kubernetes CronJob
- **UI:** Streamlit

## Learning Goals

- Log/metric anomaly detection at scale
- RAG over operational runbooks
- Prompt design for incident explanation
- Closing the observability → action loop

## Build Milestones

| Milestone | Deliverable | Est. Time |
|-----------|-------------|-----------|
| M1 | Loki + Prometheus collectors | 1 day |
| M2 | Anomaly detector (ML) | 2 days |
| M3 | K8s event correlation | 1 day |
| M4 | LLM explainer + runbook RAG | 2 days |
| M5 | Telegram alerts + dashboard | 1.5 days |

---

**Tags:** #ai #observability #logging #anomaly-detection #llm #kubernetes #devops
