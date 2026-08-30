# Real-Time Log Anomaly Detector

## Overview
A lightweight log monitoring tool that detects anomalous patterns in real-time using statistical methods and lightweight ML. Designed for homelab and small-scale deployments where full ELK stack is overkill.

## Architecture / Structure
- **Log Tailer**: Streams log entries from files, stdin, or network
- **Pattern Miner**: Discovers recurring log patterns automatically
- **Statistical Model**: Establishes baseline frequency and timing
- **Anomaly Scorer**: Computes deviation scores in sliding windows
- **Alert Dispatcher**: Notifications via Telegram, email, or webhooks
- **Dashboard**: Minimal web UI showing anomaly timeline and heatmaps

## Detection Methods
1. **Frequency Anomaly**: Unusual spike or drop in log volume
2. **Pattern Anomaly**: New log formats not seen in baseline
3. **Timing Anomaly**: Events arriving outside expected intervals
4. **Content Anomaly**: Keywords or error codes appearing unexpectedly
5. **Sequence Anomaly**: Breakdown in normal event ordering

## Workflow
1. Configure log sources (files, journald, syslog)
2. Baseline period collects normal operation patterns
3. Streaming analysis scores each incoming log entry
4. Score exceeding threshold triggers anomaly flag
5. Correlated anomalies grouped into incidents
6. Alerts sent with context: what, when, severity, similar past events
7. False positives can be marked to improve future detection

## Tools
- Python with streaming-capable libraries (streamz, river)
- SQLite for lightweight storage
- FastAPI for dashboard and API
- Telegram Bot API for alerts
- Logfmt or JSON parser for structured logs

## Learning Goals
- Real-time stream processing patterns
- Online machine learning for anomaly detection
- Lightweight monitoring for resource-constrained environments
- Alert management and noise reduction
- Log analysis at the edge

## Build Milestones
1. Week 1: Log tailing and basic pattern extraction
2. Week 2: Statistical baseline establishment from historical data
3. Week 3: Frequency and pattern anomaly detection
4. Week 4: Timing and sequence anomaly algorithms
5. Week 5: Alert dispatch with deduplication and grouping
6. Week 6: Web dashboard and API for external integration
