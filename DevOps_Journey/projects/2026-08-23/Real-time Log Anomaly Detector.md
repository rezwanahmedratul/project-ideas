# Real-time Log Anomaly Detector

**Category:** Combined (DevOps + AI)  
**Date:** 2026-08-23

---

## Overview

Build a real-time log anomaly detection system that monitors application logs for unusual patterns. Uses unsupervised ML (Isolation Forest, Autoencoders) to identify anomalies without labeled data. Integrates with Loki/Promtail and alerts via Slack when suspicious activity is detected.

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│         Real-time Log Anomaly Detector               │
│                                                     │
│  ┌──────────┐    ┌──────────────┐    ┌───────────┐  │
│  │  Logs    │───▶│  Log        │───▶│  Feature  │  │
│  │(Loki/    │    │  Streaming  │    │  Extraction│  │
│  │ file)    │    │  Collector  │    │           │  │
│  └──────────┘    └──────────────┘    └─────┬─────┘  │
│                                             │         │
│                                    ┌────────▼───────┐  │
│                                    │  Anomaly      │  │
│                                    │  Detection    │  │
│                                    │  (Isolation   │  │
│                                    │   Forest)     │  │
│                                    └───────┬───────┘  │
│                                            │           │
│                                    ┌───────▼───────┐  │
│                                    │  Alerting     │  │
│                                    │  System       │  │
│                                    └───────┬───────┘  │
│                                            │           │
│                                    ┌───────▼───────┐  │
│                                    │  Dashboard    │  │
│                                    │  (Grafana)    │  │
│                                    └──────────────┘  │
└─────────────────────────────────────────────────────┘
```

---

## Workflow

1. **Collect** logs from applications via Promtail/Fluentd
2. **Stream** logs to feature extraction pipeline
3. **Extract** features: log frequency, error rates, response times, user patterns
4. **Score** each batch using Isolation Forest
5. **Detect** anomalies when scores exceed threshold
6. **Alert** via Slack/PagerDuty with context
7. **Learn** from corrections (active learning)

---

## Tools & Stack

| Component | Technology |
|-----------|-----------|
| Log Collection | Promtail, Fluent Bit |
| Streaming | Kafka or Redis Streams |
| ML Model | Scikit-learn (Isolation Forest) |
| Database | TimescaleDB for log storage |
| Visualization | Grafana dashboards |
| Alerting | Slack webhook, PagerDuty API |

---

## Learning Goals

- Log aggregation pipelines
- Feature engineering for time series
- Unsupervised anomaly detection
- Real-time streaming processing
- ML model deployment in production
- Observability integration

---

## Build Milestones

| Phase | Deliverable | Timeline |
|-------|-------------|----------|
| 1. Collection | Promtail → Loki pipeline setup | Week 1 |
| 2. Extraction | Feature extraction from log patterns | Week 2 |
| 3. Model | Train Isolation Forest on normal behavior | Week 3 |
| 4. Detection | Real-time scoring pipeline | Week 4 |
| 5. Alerting | Slack/PagerDuty integration | Week 5 |
| 6. Dashboard | Grafana anomaly visualization | Week 6 |
| 7. Tuning | Threshold optimization + false positive reduction | Week 7 |

---

## Reference Resources

- [Promtail Documentation](https://grafana.com/docs/loki/latest/send-data/promtail/)
- [Scikit-learn Isolation Forest](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.IsolationForest.html)
- [Grafana Anomaly Detection](https://grafana.com/grafana/dashboards/)
- [Logstash/Fluentd Processing](https://www.elastic.co/guide/en/logstash/current/index.html)
