# Rust High-Performance Log Aggregator with Pattern Detection

## Overview
A high-throughput log aggregation system written in Rust that ingests logs from multiple sources, detects patterns using lightweight ML, and provides real-time alerts for anomalies.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────────┐
│                  Log Aggregator System                   │
├──────────┬──────────┬──────────┬────────────────────────┤
│ Source   │ Parser   │ Pattern  │ Alert                  │
│ Shims    │ Engine   │ Detector │ Engine                 │
├──────────┼──────────┼──────────┼────────────────────────┤
│          │          │ Storage  │ Visualization          │
│ (File,   │ (Regex,  │ (Parquet,│ (Grafana,              │
│  Syslog, │  ML     │  ClickHouse)│  Web UI)             │
│  TCP)    │  Parse)  │          │                        │
└──────────┴──────────┴──────────┴────────────────────────┘
```

## Workflow
1. Source shims collect logs from file tails, syslog, TCP sockets
2. Parser engine extracts structured fields using regex + ML
3. Pattern detector runs lightweight anomaly detection (Isolation Forest)
4. Aggregated data stored in Parquet/ClickHouse for analysis
5. Alerts triggered on pattern matches or threshold breaches

## Tools
- Rust (Tokio for async)
- ClickHouse for storage
- Apache Arrow for in-memory processing
- Isolation Forest for anomaly detection
- Grafana for visualization

## Learning Goals
- Rust async programming patterns
- High-throughput data pipeline design
- Time-series anomaly detection
- ClickHouse query optimization

## Build Milestones
1. **M1**: Single source log ingestion with file tail
2. **M2**: Structured parsing with regex engine
3. **M3**: Pattern detection with Isolation Forest
4. **M4**: ClickHouse storage integration
5. **M5**: Multi-source aggregation (syslog, TCP)
6. **M6**: Real-time dashboard with Grafana integration
