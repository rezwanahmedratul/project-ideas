# AI Kubernetes Cost-Aware Autoscaler

**Category:** Combined (DevOps + AI/ML)  
**Date:** 2026-08-19  
**Difficulty:** Advanced  

## Overview
A custom autoscaler that uses a lightweight ML model to **predict traffic and right-size pods/node pools** instead of reacting to thresholds after the fact. It learns daily/weekly patterns from Prometheus metrics and pre-scales before peaks, cutting cloud cost while maintaining latency. A practical merge of Kubernetes ops and time-series forecasting.

## Architecture / Structure
```
cost-autoscaler/
├── metrics/              # Prometheus query client
├── forecast.py           # time-series model (Prophet/ARIMA/LSTM-lite)
├── planner.py            # translate forecast -> desired replicas/nodes
├── controller.py         # apply via K8s API, respect budgets
├── policies.yaml         # max/min, budget caps, cooldowns
├── deploy/               # RBAC + Deployment
└── README.md
```

## Workflow
1. Scrape historical CPU/requests/latency from Prometheus.
2. Train/refresh a forecasting model on the traffic curve.
3. Planner converts the next-hour forecast into desired replica & node counts within policy bounds.
4. Controller applies changes via the Kubernetes API ahead of predicted load.
5. Actual vs. predicted is logged to improve the model and report savings.

## Tools
- Python, Kubernetes Python client, Prometheus API
- `prophet` or `statsmodels` (ARIMA) or a tiny LSTM
- Metrics-server / Prometheus + Grafana
- RBAC, Deployment manifest

## Learning Goals
- Time-series forecasting for ops.
- Programmatic Kubernetes control (client-go/python).
- Cost/latency trade-off engineering.
- Closed-loop control with safety bounds.

## Build Milestones
1. Pull Prometheus series and visualize the traffic pattern.
2. Train a forecaster and validate on a holdout week.
3. Implement the planner + controller applying replica changes.
4. Add node-pool scaling + budget/policy guards.
5. Measure cost/latency vs. default HPA over a 2-week run.
