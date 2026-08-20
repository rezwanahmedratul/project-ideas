# Homelab Observability Stack

**Category:** DevOps  
**Date:** 2026-08-19  
**Difficulty:** Beginner–Intermediate  

## Overview
A single, reproducible deployment that stands up a **full observability stack** for a homelab: metrics (Prometheus), logs (Loki + Promtail), traces (Tempo or Grafana Alloy), and dashboards (Grafana). Goal: one `make up` gives you a unified view of every container, VM, and service you run at home — and teaches the three pillars of observability end to end.

## Architecture / Structure
```
observability-stack/
├── docker-compose.yml   # Prometheus, Grafana, Loki, Alloy
├── prometheus/
│   └── prometheus.yml   # scrape configs for homelab services
├── loki/
│   └── loki-config.yaml
├── alloy/
│   └── config.alloy     # logs + metrics + traces collector
├── dashboards/          # JSON dashboards (node, docker, app)
├── alerts/              # alert rules
└── Makefile
```

## Workflow
1. `make up` launches the stack via Docker Compose.
2. Alloy scrapes node_exporter, cAdvisor, and app metrics; ships logs to Loki.
3. Prometheus evaluates alert rules; Grafana visualizes everything.
4. New homelab services are added to scrape configs and get a dashboard.

## Tools
- Docker Compose
- Prometheus, Grafana, Loki, Grafana Alloy (or Tempo)
- node_exporter, cAdvisor
- Alertmanager (optional)

## Learning Goals
- The three pillars: metrics, logs, traces.
- Prometheus query language (PromQL).
- Log aggregation and label-based correlation.
- Building reusable dashboards.

## Build Milestones
1. Launch Prometheus + Grafana + node_exporter; graph CPU/mem.
2. Add Loki + Promtail; correlate a log line with a metric spike.
3. Add cAdvisor + Docker container dashboards.
4. Write 3 alert rules (disk full, container down, high CPU).
5. Template the stack so a friend can `git clone && make up`.
