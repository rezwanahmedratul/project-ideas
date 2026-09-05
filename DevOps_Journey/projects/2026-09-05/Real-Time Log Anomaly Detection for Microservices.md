# Real-Time Log Anomaly Detection for Microservices

## Overview

Build a real-time log analysis system that detects anomalies in microservice architectures using statistical methods and lightweight ML. Provides early warning for production issues before they impact users.

## Architecture

```
┌─────────────────────────────────────────────┐
│        Log Anomaly Detection System          │
│                                             │
│  ┌──────────┐  ┌──────────────────────┐    │
│  │ Log      │  │ Schema Parser        │    │
│  │ Sources  │  │ (structured extraction)│   │
│  │ (Promtail)│  └──────────────────────┘    │
│  └──────────┘            ↓                 │
│                        ┌─────────────┐     │
│                        │ Feature     │     │
│                        │ Extractor   │     │
│                        └─────────────┘     │
│                             ↓              │
│  ┌─────────────────────────────────────┐   │
│  │   Anomaly Detection Engine         │   │
│  │   - Statistical baselines          │   │
│  │   - Pattern deviation detection    │   │
│  │   - Correlation analysis           │   │
│  └─────────────────────────────────────┘   │
│                             ↓              │
│  ┌─────────────┐  ┌──────────────────────┐  │
│  │ Alerting    │  │ Dashboard            │  │
│  │ (PagerDuty) │  │ (Grafana)            │  │
│  └─────────────┘  └──────────────────────┘  │
└─────────────────────────────────────────────┘
```

## Workflow

1. **Ingestion**: Collect logs from all microservices via Promtail or Fluent Bit
2. **Parsing**: Extract structured fields (service, level, message template, duration)
3. **Feature Engineering**: Compute rates, distributions, and correlations
4. **Detection**: Apply statistical tests and pattern matching for anomaly identification
5. **Alerting**: Escalate confirmed anomalies with context-rich notifications

## Tools

- Loki for log aggregation
- Promtail for log shipping
- Python with pandas/scipy for analysis
- Alertmanager for notification routing
- Grafana for visualization

## Learning Goals

- Understand log-based anomaly detection patterns
- Learn statistical process control for monitoring
- Master log aggregation architecture at scale
- Practice incident response workflow design

## Build Milestones

1. **Week 1**: Set up log collection from multiple services
2. **Week 2**: Implement log parsing and feature extraction
3. **Week 3**: Build baseline detection algorithms
4. **Week 4**: Create anomaly correlation and root cause identification
5. **Week 5**: Integrate alerting and build operational dashboard
