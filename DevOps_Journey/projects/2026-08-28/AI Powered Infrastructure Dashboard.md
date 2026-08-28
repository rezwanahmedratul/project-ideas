# Combined: AI-Powered Infrastructure Dashboard

## Overview
Build a unified dashboard that monitors cloud infrastructure (Kubernetes pods, Lambda functions, RDS instances) and uses AI to predict failures, suggest optimizations, and generate natural-language status reports.

## Architecture
```
Infrastructure APIs
   ├── Kubernetes API → Metrics Aggregator
   ├── AWS CloudWatch → Metrics Aggregator
   ├── Azure Monitor  → Metrics Aggregator
                         ↓
                  Time-Series Store (TimescaleDB)
                         ↓
              AI Analysis Engine
   ├── Anomaly Detection (Prophet/Isolation Forest)
   ├── Failure Prediction (LSTM / Transformer)
   └── Report Generator (LLM summarization)
                         ↓
               Dashboard (Grafana + Custom UI)
```

## Workflow
1. Aggregate metrics from K8s, AWS, Azure every 30s
2. Feed time-series data to anomaly detection models
3. LLM generates daily status report from metric trends
4. Dashboard displays real-time health + AI insights
5. Alerts fire when predicted failure probability exceeds threshold

## Tools
Python, TimescaleDB, Grafana, Prometheus, FastAPI, Claude API, Kubernetes API, AWS SDK

## Learning Goals
- Multi-source metrics aggregation
- Time-series anomaly detection
- LLM-powered reporting and summarization
- Full-stack observability dashboard design

## Build Milestones
1. Connect to K8s and AWS metrics APIs
2. Build unified time-series storage layer
3. Implement anomaly detection on key metrics
4. Add LLM-generated daily status reports
5. Create unified dashboard with anomaly overlays and predictions
