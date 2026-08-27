# Real-Time Log Anomaly Detector with Stream Processing

**Date:** 2026-08-27
**Category:** Combined (DevOps + AI)
**Tags:** log-analysis, stream-processing, anomaly-detection, kafka, ml

---

## Overview

Build a real-time log analysis system that ingests application and infrastructure logs, detects anomalies using unsupervised ML, and alerts on suspicious patterns — all streaming, no batch delays.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                   Log Sources                                │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌──────────────────┐  │
│  │ App     │ │ System  │ │ K8s     │ │ Firewall/Proxy   │  │
│  │ Logs    │ │ Logs    │ │ Events  │ │ Logs             │  │
│  └────┬────┘ └────┬────┘ └────┬────┘ └────────┬─────────┘  │
│       │            │            │               │           │
│       └────────────┴─────┬─────┴───────────────┘           │
│                          ▼                                  │
│              ┌───────────────────────┐                      │
│              │    Log Collector      │                      │
│              │  (Fluentd/Vector)     │                      │
│              └───────────┬───────────┘                      │
│                          ▼ Kafka Topic                      │
│              ┌───────────────────────┐                      │
│              │     Stream Processor   │                      │
│              │  ┌─────────────────┐   │                      │
│              │  │  Feature Eng    │   │                      │
│              │  │  (Windowing,    │   │                      │
│              │  │   Batching)     │   │                      │
│              │  └────────┬────────┘   │                      │
│              │  ┌────────▼────────┐   │                      │
│              │  │  Anomaly Model  │   │                      │
│              │  │  (Isolation    │   │                      │
│              │  │   Forest /     │   │                      │
│              │  │   Autoencoder) │   │                      │
│              │  └────────┬────────┘   │                      │
│              │  ┌────────▼────────┐   │                      │
│              │  │  Alert Engine   │   │                      │
│              │  └─────────────────┘   │                      │
│              └───────────────────────┘                      │
│                          ▼                                  │
│              ┌───────────────────────┐                      │
│              │  Alerts: Slack,       │                      │
│              │  PagerDuty, Grafana   │                      │
│              └───────────────────────┘                      │
└─────────────────────────────────────────────────────────────┘
```

## Log Categories & Features

| Source | Features Extracted |
|--------|-------------------|
| Application | Error rate, response time percentiles, request count, status code distribution |
| System | CPU spikes, memory pressure, disk I/O, network errors |
| Kubernetes | Pod restarts, OOM kills, eviction events, node conditions |
| Proxy/Firewall | Connection drops, unusual source IPs, blocked requests |

## Anomaly Detection Models

### Statistical Baseline
- Moving average with confidence intervals
- Seasonal decomposition (time-of-day patterns)
- Z-score on aggregated metrics

### Machine Learning
- **Isolation Forest** — Identifies rare feature combinations
- **Autoencoder** — High reconstruction error = anomaly
- **One-Class SVM** — Boundary around normal data

### Pattern-Based Detection
- Sudden spike in error rate (>3σ from baseline)
- New error patterns never seen before
- Sequence anomalies (unusual order of events)

## Windowing Strategy

```
Sliding Windows:
- 1-minute window: Fast detection (security incidents)
- 5-minute window: Operational anomalies
- 15-minute window: Trending/degrading systems
- Hourly aggregation: Capacity planning signals
```

## Alert Tiers

| Tier | Condition | Response |
|------|-----------|----------|
| **Critical** | Service down, data loss risk | PagerDuty + Slack + auto-escalation |
| **Warning** | Degraded performance, unusual patterns | Slack notification + ticket |
| **Info** | Minor deviation, likely transient | Logged for review |

## Tech Stack

| Component | Technology |
|-----------|------------|
| Log collection | Vector (formerly Fluent Bit successor) or Fluentd |
| Message queue | Apache Kafka or Redpanda |
| Stream processing | Faust (Python) or ksqlDB |
| ML models | scikit-learn, PyTorch (autoencoders) |
| Storage | ClickHouse (log storage) or TimescaleDB |
| Visualization | Grafana with Loki datasources |
| Alerting | Alertmanager + webhook integrations |

## Deployment Options

1. **On-premise**: Full self-hosted stack on Kubernetes
2. **Hybrid**: Kafka on-prem, ML training in cloud
3. **Cloud-native**: MSK/KDA or equivalent managed services

## Learning Goals

- Stream processing architectures
- Real-time feature engineering
- Unsupervised anomaly detection
- Kafka producer/consumer patterns
- Log aggregation at scale

## Build Milestones

1. [ ] Set up Kafka cluster and log ingestion pipeline
2. [ ] Build feature extraction from raw log streams
3. [ ] Implement statistical baseline calculations
4. [ ] Train Isolation Forest model on historical data
5. [ ] Deploy autoencoder for complex pattern detection
6. [ ] Create alert routing with tiered thresholds
7. [ ] Build Grafana dashboards for anomaly visualization
8. [ ] Add self-learning: feed confirmed anomalies back to training
9. [ ] Containerize and deploy on Kubernetes

---
*Generated: 2026-08-27*
