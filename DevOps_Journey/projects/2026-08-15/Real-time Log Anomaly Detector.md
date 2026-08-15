# Real-time Log Anomaly Detector

## Overview
A streaming log analysis system that detects anomalies in real-time using statistical methods and ML models.

## Architecture
```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Log       │     │  Streaming  │     │  Anomaly    │
│   Sources   │────▶│  Engine     │────▶│  Detector   │
│  (K8s,     │     │  (Kafka,    │     │  (ML Model) │
│   Docker)   │     │   Flink)    │     └─────────────┘
└─────────────┘     └─────────────┘            │
                                              ┌───────────┐
                                              │  Alerting │
                                              │  System   │
                                              └───────────┘
```

## Workflow
1. **Ingest**: Collect logs from multiple sources
2. **Stream**: Process logs in real-time streams
3. **Analyze**: Compute statistics and detect patterns
4. **Detect**: Identify anomalies using ML models
5. **Alert**: Notify on significant deviations

## Tools
- Apache Kafka or Redis Streams
- Python with pandas/scikit-learn
- Elasticsearch for storage
- Grafana for visualization
- Prometheus for metrics

## Learning Goals
- Learn stream processing patterns
- Practice real-time anomaly detection
- Understand log analysis techniques
- Build monitoring systems at scale

## Build Milestones
1. **M1**: Basic log ingestion and storage
2. **M2**: Implement streaming analysis
3. **M3**: Add statistical anomaly detection
4. **M4**: Integrate ML models for pattern learning
5. **M5**: Build alerting and notification system
6. **M6**: Create dashboard with real-time visualization
