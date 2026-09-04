# Real-Time Log Anomaly Detector for Microservices

## Overview
A streaming log analysis system that detects anomalies in microservice log patterns in real-time, alerting on unusual error rates, latency spikes, and unexpected log sequences.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────────┐
│          Real-Time Log Anomaly Detector                   │
├─────────────┬──────────────┬──────────────┬─────────────┤
│  Log        │  Stream      │  Anomaly     │  Alert      │
│  Ingestion  │    Engine    │  Detector    │  Manager    │
├─────────────┴──────────────┴──────────────┴─────────────┤
│              Kafka/Pulsar + ClickHouse                   │
└─────────────────────────────────────────────────────────┘
```

## Workflow
1. Log ingestion captures streaming logs from all microservices
2. Stream engine performs real-time feature extraction (error rates, latency percentiles)
3. Anomaly detector applies statistical tests and ML models to identify outliers
4. Alert manager routes notifications based on severity and service criticality
5. Feedback loop improves detection accuracy over time

## Tools
- Apache Kafka or Pulsar for streaming
- ClickHouse for real-time analytics
- Python (scikit-learn, PyTorch) for anomaly detection
- FastAPI for alerting endpoints
- Slack/Telegram integration for notifications

## Learning Goals
- Stream processing architectures
- Real-time anomaly detection algorithms
- Microservice observability patterns
- Alert routing and on-call integration

## Build Milestones
1. **M1**: Log ingestion from file and syslog
2. **M2**: Real-time stream processing with Kafka
3. **M3**: Basic statistical anomaly detection
4. **M4**: ML-based pattern recognition
5. **M5**: Multi-service correlation analysis
6. **M6**: Automated incident response integration
