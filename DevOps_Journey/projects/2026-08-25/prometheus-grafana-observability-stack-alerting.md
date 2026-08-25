# Project: Prometheus + Grafana Observability Stack with Alerting

## Overview
Deploy a complete observability stack using Prometheus for metrics collection, Grafana for visualization, and Alertmanager for notifications. Monitor Docker containers, Kubernetes pods, and bare-metal servers with custom exporters and dashboards.

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│  Monitoring Stack (Docker Compose)                  │
│  ┌──────────┐  ┌────────────┐  ┌──────────────┐   │
│  │Prometheus│  │ Alertmanager│  │  Grafana     │   │
│  │  :9090   │  │   :9093    │  │   :3000      │   │
│  └────┬─────┘  └─────┬──────┘  └──────┬───────┘   │
│       │              │                │            │
│  ┌────▼─────┐  ┌─────▼──────┐  ┌─────▼───────┐   │
│  │ Node_Exp │  │  Pushgateway│  │  Alert Rules │   │
│  │Exporter  │  │ (batch jobs)│  │  (recording) │   │
│  └──────────┘  └────────────┘  └─────────────┘   │
├─────────────────────────────────────────────────────┤
│  Targets (exporters on monitored systems)           │
│  ├── Node Exporter (Linux metrics)                  │
│  ├── cAdvisor (Docker container metrics)            │
│  ├── Blackbox Exporter (HTTP/TCP probing)           │
│  └── Redis Exporter (Redis instance metrics)        │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Deploy stack via Docker Compose (Prometheus, Grafana, Alertmanager, exporters)
2. Configure `prometheus.yml` scrape jobs for each exporter
3. Create Grafana datasources (Prometheus, Loki for logs)
4. Import pre-built dashboards (Node Exporter Full, Kubernetes Cluster)
5. Define alert rules: high CPU (>80%), disk >90%, container OOM, service down
6. Configure Alertmanager routes: PagerDuty for critical, Slack for warnings
7. Set up Blackbox probes for external endpoint availability checks
8. Add recording rules to pre-compute expensive queries

## Tools
- **Prometheus** (time-series database + query language PromQL)
- **Grafana** (dashboards + templating)
- **Alertmanager** (routing, grouping, inhibition)
- **Node Exporter**, **cAdvisor**, **Blackbox Exporter**
- **Loki** (optional: log aggregation sidecar)
- **docker-compose** (single-file deployment)

## Learning Goals
- PromQL queries and aggregations (rate, histogram_quantile, up)
- Prometheus job discovery and relabeling
- Grafana template variables and panel linking
- Alert rule syntax and inhibition rules
- Recording rules for performance optimization
- External service probing with Blackbox Exporter

## Build Milestones
1. [ ] Write docker-compose.yml with all core components
2. [ ] Start exporters; verify Prometheus can scrape them
3. [ ] Build Grafana dashboard: system overview (CPU, RAM, disk)
4. [ ] Add container-level metrics (cAdvisor)
5. [ ] Write 5+ alert rules with correct severity labels
6. [ ] Configure Alertmanager → Slack webhook integration
7. [ ] Set up Blackbox probe for external URL health check
8. [ ] Create a Grafana dashboard for alert summary view

## References
- https://prometheus.io/docs/introduction/overview/
- https://grafana.com/docs/grafana/latest/dashboards/
