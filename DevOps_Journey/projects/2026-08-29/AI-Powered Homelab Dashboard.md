# AI-Powered Homelab Dashboard

## Overview
A unified monitoring dashboard for homelab services that combines infrastructure metrics, application health, and AI-generated insights into a single pane of glass. Automatically detects anomalies and suggests remediation actions based on historical patterns.

## Architecture / Structure
- **Metrics Collector**: Scrapes Prometheus endpoints from all homelab services
- **Health Checker**: Probes critical services (DNS, docker, proxmox, k8s) via HTTP/API
- **AI Analyzer**: Detects anomalies in metrics and correlates across services
- **Dashboard**: Grafana-style panel with custom widgets and AI insight cards
- **Alert Manager**: Sends Telegram/WhatsApp notifications with context

## Workflow
1. Collect metrics from Prometheus, node_exporter, cAdvisor
2. Aggregate service health scores from custom probes
3. AI model identifies unusual patterns (e.g., disk growth spike correlated with log rotation failure)
4. Dashboard displays current state with trend indicators
5. AI insights card shows "Detected anomaly in storage — recommend checking /var/log rotation"
6. Alert triggered via Telegram webhook if severity exceeds threshold

## Tools
- Prometheus + Grafana for metrics and dashboards
- Python FastAPI for AI analysis service
- Ollama + local LLM for natural language insights
- Telegram Bot API for alerts
- Docker Compose for homelab service orchestration

## Learning Goals
- Prometheus metric collection and alerting rules
- Anomaly detection in time-series data
- Multi-service observability patterns
- AI-assisted operations (AIOps) concepts

## Build Milestones
1. Week 1: Prometheus scraping configuration for all services
2. Week 2: Health check probes with alerting rules
3. Week 3: Grafana dashboard with custom panels
4. Week 4: AI anomaly detection service with Ollama
5. Week 5: Telegram alert integration with message formatting
6. Week 6: Unified dashboard with AI insights cards
