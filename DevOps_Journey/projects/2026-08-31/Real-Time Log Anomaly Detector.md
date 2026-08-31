# Real-Time Log Anomaly Detector

**Category:** Combined  
**Date:** 2026-08-31

## Overview
A streaming log analysis system that detects anomalies in real-time using statistical baselines and ML, alerting on deviations before they become incidents.

## Architecture
```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  Log Stream     │────▶│  Baseline       │────▶│  Anomaly       │
│  (kafka/pipe)   │     │  Learner        │     │  Detector      │
└─────────────────┘     └─────────────────┘     └────────┬────────┘
                                                        │
                                              ┌────────▼────────┐
                                              │  Alert /       │
                                              │  Dashboard     │
                                              └─────────────────┘
```

## Workflow
1. Stream logs in real-time from services
2. Maintain running baselines for log frequency, patterns, error rates
3. Detect deviations using statistical methods (z-score, isolation forest)
4. Alert on significant anomalies
5. Dashboard shows anomaly timeline and correlation

## Tools
- Python (faust or kafka-python for streaming)
- Scikit-learn for anomaly detection
- SQLite for baseline storage
- WebSocket for real-time dashboard

## Learning Goals
- Stream processing patterns
- Online learning and baselining
- Anomaly detection algorithms
- Real-time alerting systems

## Build Milestones
- [ ] Week 1: Log stream ingestion
- [ ] Week 2: Baseline calculation and storage
- [ ] Week 3: Statistical anomaly detection
- [ ] Week 4: ML-based detection (isolation forest)
- [ ] Week 5: Real-time alerting
- [ ] Week 6: Dashboard with anomaly timeline
