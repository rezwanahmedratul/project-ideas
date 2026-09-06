# Real-Time Log Anomaly Detection for Microservices

## Overview
Implement a real-time anomaly detection system for microservice logs using unsupervised ML, identifying unusual patterns before they become incidents.

## Architecture
```
┌─────────────────────────────────────────┐
│    Log Anomaly Detection System         │
├─────────────────────────────────────────┤
│  Log Ingestion                          │
│  ├─ Kafka or Fluentbit                  │
│  ├─ Log parsing (regex/patterns)        │
│  └─ Structured feature extraction       │
├─────────────────────────────────────────┤
│  Anomaly Engine                         │
│  ├─ Isolation Forest / LODA             │
│  ├─ Pattern baseline learning           │
│  └─ Real-time scoring                   │
├─────────────────────────────────────────┤
│  Alerting                               │
│  ├─ Severity classification             │
│  ├─ Deduplication                       │
│  └─ PagerDuty/Slack integration         │
└─────────────────────────────────────────┘
```

## Workflow
1. Logs flow from services into Kafka
2. Parser extracts structured features
3. Anomaly model scores each log entry
4. High-scoring entries trigger alerts
5. Trends analyzed for emerging issues

## Tools
- Apache Kafka or Redpanda
- Python (scikit-learn, PyOD)
- Elasticsearch for log storage
- Grafana for visualization

## Learning Goals
- Stream processing architectures
- Unsupervised anomaly detection
- Log pattern analysis
- Real-time alerting systems

## Build Milestones
- [ ] Week 1: Log ingestion pipeline
- [ ] Week 2: Feature extraction
- [ ] Week 3: Baseline model training
- [ ] Week 4: Real-time scoring
- [ ] Week 5: Alert integration
- [ ] Week 6: Accuracy evaluation
