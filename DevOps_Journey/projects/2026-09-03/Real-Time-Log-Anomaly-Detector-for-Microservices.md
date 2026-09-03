# Real-Time Log Anomaly Detector for Microservices
**Date:** 2026-09-03  
**Category:** Combined  
**Complexity:** Advanced

---

## Overview

Build a real-time anomaly detection system that monitors microservice logs, identifies unusual patterns automatically, and alerts on potential issues before they impact users.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│            Real-Time Log Anomaly Detector                   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Log Sources                                                │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │ Service A│  │ Service B│  │ Service C│  │ Gateway  │  │
│  │ (stdout) │  │ (stderr) │  │ (file)   │  │ (access) │  │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘  │
│       │             │             │             │          │
│       └─────────────┴─────────────┴─────────────┘          │
│                            │                               │
│                    ┌───────▼───────────┐                   │
│                    │   Log Aggregator  │                   │
│                    │   • Fluentd       │                   │
│                    │   • Filebeat      │                   │
│                    │   • Vector        │                   │
│                    └───────┬───────────┘                   │
│                            │                               │
│                    ┌───────▼───────────┐                   │
│                    │   Stream Processor│                   │
│                    │   • Kafka/Kinesis │                   │
│                    │   • Schema parse  │                   │
│                    │   • Enrichment    │                   │
│                    └───────┬───────────┘                   │
│                            │                               │
│                    ┌───────▼───────────┐                   │
│                    │   Feature Engine  │                   │
│                    │   • Log parsing   │                   │
│                    │   • Metric extr.  │                   │
│                    │   • Template mat. │                   │
│                    └───────┬───────────┘                   │
│                            │                               │
│  Anomaly Detection Layer                                    │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  • Statistical: Z-score, IQR, EWMA                 │   │
│  │  • ML: Isolation Forest, LOF, Autoencoders         │   │
│  │  • Pattern: Regex matching, keyword frequency      │   │
│  │  • Temporal: Rate-of-change, burst detection       │   │
│  └─────────────────────────────────────────────────────┘   │
│                           │                                 │
│                    ┌──────▼───────────┐                    │
│                    │   Alert Engine    │                    │
│                    │   • Thresholds   │                    │
│                    │   • Correlation  │                    │
│                    │   • Deduplication│                    │
│                    └──────┬───────────┘                    │
│                           │                                │
│                    ┌──────▼───────────┐                    │
│                    │   Notification    │                    │
│                    │   • Slack/Teams  │                    │
│                    │   • PagerDuty    │                    │
│                    │   • Email        │                    │
│                    └──────────────────┘                    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## Anomaly Types Detected

### Error Spikes
```python
# Detect sudden increase in error rate
error_rate_window = get_errors(last_5_minutes)
error_rate_baseline = get_errors(last_1_hour_average)

if error_rate_window > error_rate_baseline * 3:
    trigger_alert(
        severity="high",
        message=f"Error rate spiked {error_rate_window/error_rate_baseline}x",
        service=service_name
    )
```

### Log Template Changes
- New log patterns appearing unexpectedly
- Missing expected log entries
- Format changes indicating code modifications

### Latency Anomalies
- Response time increases correlated with log messages
- Timeout patterns emerging
- Slow query indicators

### Cascading Failure Detection
```
Service A failure → Service B errors → Service C timeouts
         ↓                    ↓                  ↓
    [ROOT CAUSE]        [SYMPTOM 1]       [SYMPTOM 2]
```

## Detection Algorithms

| Algorithm | Use Case | Strength | Weakness |
|-----------|----------|----------|----------|
| **Isolation Forest** | General anomalies | Fast, no labeling | False positives |
| **LOF** | Local density | Good for clusters | Slower computation |
| **EWMA Control Chart** | Rate monitoring | Simple, effective | Assumes stationarity |
| **Autoencoder** | Complex patterns | Learns normality | Requires training data |

## Implementation Example

```python
from sklearn.ensemble import IsolationForest
import numpy as np

class LogAnomalyDetector:
    def __init__(self, contamination=0.05):
        self.model = IsolationForest(
            contamination=contamination,
            random_state=42,
            n_estimators=100
        )
        self.feature_cache = {}
    
    def extract_features(self, log_entry: dict) -> np.ndarray:
        """Convert log to numerical features"""
        features = [
            log_entry['severity_score'],
            log_entry['response_time_ms'],
            log_entry['error_code_numeric'],
            len(log_entry['message'].split()),
            hash(log_entry['template']) % 1000,
        ]
        return np.array(features)
    
    def detect(self, log_entry: dict) -> bool:
        features = self.extract_features(log_entry)
        prediction = self.model.predict([features])
        return prediction[0] == -1  # -1 means anomaly
```

## Tools & Technologies

- **Python** with scikit-learn for ML
- **Apache Kafka** or **AWS Kinesis** for streaming
- **Fluentd** or **Vector** for log collection
- **Prometheus** for metric storage
- **Grafana** for visualization
- **Alertmanager** for alert routing

## Learning Goals

- Design real-time stream processing pipelines
- Apply unsupervised learning to log analysis
- Build correlated alerting systems
- Master log parsing and template extraction
- Implement production-grade monitoring

## Build Milestones

| Milestone | Description |
|-----------|-------------|
| M1 | Set up log ingestion with Fluentd/Filebeat |
| M2 | Build log parser and feature extractor |
| M3 | Implement statistical anomaly detection |
| M4 | Add ML-based detection with Isolation Forest |
| M5 | Build correlation engine for root cause |
| M6 | Create dashboard and notification system |

## Reference Links

- [ELK Stack Documentation](https://www.elastic.co/what-is/elk-stack)
- [Scikit-learn Isolation Forest](https://scikit-learn.org/stable/modules/isolation_forest.html)
- [Promtail Log Aggregator](https://grafana.com/docs/loki/latest/send-loki/promtail/)
- [Anomaly Detection in Logs Survey](https://arxiv.org/abs/2006.xxxxx)
