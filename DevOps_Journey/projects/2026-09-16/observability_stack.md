# Project: Observability Stack with Prometheus, Grafana & Loki

## Overview
Deploy a complete observability platform combining metrics (Prometheus), visualization (Grafana), and log aggregation (Loki). Monitor a microservices application with distributed tracing via Jaeger.

## Architecture
```
┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐
│ Service A│    │ Service B│    │ Service C│    │  Service │
│  (Go)    │    │  (Python)│    │  (Node)  │    │  (Rust)  │
└────┬─────┘    └────┬─────┘    └────┬─────┘    └────┬─────┘
     │               │               │               │
     └───────────────┴───────────────┴───────────────┘
                          │
                    Exporters/Agents
                          │
     ┌────────────────────┼────────────────────┐
     ▼                    ▼                    ▼
┌──────────┐        ┌──────────┐        ┌──────────┐
│Prometheus│        │   Loki   │        │  Tempo   │
│ (metrics)│        │ (logs)   │        │(traces)  │
└────┬─────┘        └────┬─────┘        └────┬─────┘
     │                   │                   │
     └───────────────────┴───────────────────┘
                          │
                     ┌──────────┐
                     │ Grafana  │
                     │(dashboard│
                     │& alerts) │
                     └──────────┘
```

## Workflow
1. Services emit metrics (OpenMetrics), logs, and traces
2. Collectors aggregate data into Prometheus, Loki, Tempo
3. Grafana provides unified dashboards
4. Alertmanager handles notifications (Slack, email, PagerDuty)

## Tools & Tech Stack
- **Prometheus** — Metrics collection and alerting
- **Grafana** — Visualization and dashboards
- **Loki** — Log aggregation (Lightweight, no index)
- **Alertmanager** — Alert routing and silencing
- **Promtail** — Log agent for Loki
- **Jaeger/Tempo** — Distributed tracing
- **Node Exporter** — Host-level metrics

## Learning Goals
- Prometheus query language (PromQL)
- Grafana dashboard design and templating
- Log aggregation patterns
- Alert rules and notification channels
- SLO/SLI definition and tracking

## Build Milestones
1. [ ] Deploy stack via Docker Compose
2. [ ] Instrument Python FastAPI service
3. [ ] Create custom dashboards for each service
4. [ ] Set up log pipelines with Promtail → Loki
5. [ ] Configure distributed tracing
6. [ ] Define SLO-based alert rules
7. [ ] Test failover and recovery scenarios

## Reference Links
- [Prometheus Documentation](https://prometheus.io/docs/)
- [Grafana Documentation](https://grafana.com/docs/)
- [Loki Documentation](https://grafana.com/oss/loki/)
- [Awesome Monitoring Dashboards](https://grafana.com/grafana/dashboards/)
