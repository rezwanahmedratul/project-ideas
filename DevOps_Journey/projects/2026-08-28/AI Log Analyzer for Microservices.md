# Combined: AI Log Analyzer for Microservices

## Overview
Build a service that ingests logs from multiple microservices, uses AI to detect error patterns and correlate incidents across services, and surfaces actionable insights — reducing mean time to resolution (MTTR) for distributed system outages.

## Architecture
```
Log Sources
   ├── Kubernetes pods (stdout/stderr)
   ├── Application loggers (structured JSON)
   ├── System logs (journald)
         ↓
   Log Ingestion (Fluent Bit → Kafka)
         ↓
   AI Analysis Engine
   ├── Log clustering (similarity-based grouping)
   ├── Anomaly detection (temporal pattern breaking)
   ├── Cross-service correlation (causal inference)
   └── Root cause suggestion (LLM on clustered errors)
         ↓
   Alert + Dashboard (Grafana + custom UI)
```

## Workflow
1. Fluent Bit ships logs from all services to a central store
2. AI engine clusters similar log entries in real-time
3. Detects anomalous spikes in error rates per service
4. Correlates errors across service boundaries to find cascade patterns
5. Generates incident summary with likely root cause and affected services

## Tools
Python, Elasticsearch or Loki, Flask/FastAPI, sentence-transformers, Grafana, Fluent Bit, Kafka

## Learning Goals
- Distributed log aggregation architecture
- Log clustering and pattern recognition
- Cross-service dependency mapping
- Real-time anomaly detection pipelines

## Build Milestones
1. Set up Fluent Bit → Loki/Elasticsearch log pipeline
2. Implement log clustering using embedding similarity
3. Add temporal anomaly detection on error rates
4. Build cross-service correlation engine
5. Create alerting dashboard with incident summaries
