# Prometheus Anomaly Detection Alerting

**Category:** DevOps  
**Date:** 2026-08-18  
**Difficulty:** Intermediate

---

## Overview

A service that sits alongside Prometheus and uses statistical/ML methods to detect anomalies in time-series metrics (CPU, memory, request latency, error rates) and generates smart alerts with root-cause hints. Reduces alert fatigue from static thresholds in homelab K8s clusters.

## Architecture / Structure

```
anomaly-alerting/
├── cmd/
│   └── server/            # HTTP API + Prometheus poll loop
├── internal/
│   ├── collector/        # Prometheus query client
│   ├── detector/         # EWMA/Z-score/IsolationForest
│   ├── correlator/       # Cross-metric correlation
│   └── notifier/         # AlertManager/Telegram
├── models/               # Trained models (joblib/pickle)
├── config/
│   └── rules.yaml        # Metric → algorithm mapping
└── deploy/
    └── k8s.yaml          # Deployment + ServiceMonitor
```

## Workflow

1. **Collector** queries Prometheus every 30s for watched metrics
2. **Detector** applies per-metric algorithm (Z-score for steady, EWMA for seasonal)
3. **Correlator** checks if multiple metrics spike together (e.g., CPU + latency)
4. **Notifier** sends enriched alert: metric, deviation %, likely cause, graph link
5. **Feedback** loop: user marks false positive → model retrains

## Tools

- **Metrics:** Prometheus, PromQL
- **ML:** Python (scikit-learn, statsmodels), numpy
- **Serving:** FastAPI, uvicorn
- **Alerting:** AlertManager, Telegram Bot API
- **Deploy:** Kubernetes, Helm chart

## Learning Goals

- PromQL querying and range vectors
- Time-series anomaly detection algorithms
- Statistical baselining vs. ML approaches
- Reducing false positives via correlation

## Build Milestones

| Milestone | Deliverable | Est. Time |
|-----------|-------------|-----------|
| M1 | Prometheus client + metric polling | 0.5 day |
| M2 | Z-score detector + static alerts | 1 day |
| M3 | EWMA seasonal detector | 1 day |
| M4 | Cross-metric correlation | 1.5 days |
| M5 | Telegram/AlertManager integration | 0.5 day |
| M6 | Helm deploy + Grafana panel | 1 day |

---

**Tags:** #prometheus #monitoring #anomaly-detection #ml #kubernetes #alerting
