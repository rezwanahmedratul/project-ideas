# Proxmox Cluster Monitor with Grafana Dashboard

**Date:** 2026-09-13  
**Category:** DevOps  
**Difficulty:** Intermediate

---

## Overview

Build a comprehensive monitoring solution for a Proxmox VE cluster using Prometheus and Grafana. The dashboard will track VM performance, storage utilization, network throughput, and alert on anomalies.

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                  Grafana Dashboard                   │
└─────────────────────────────────────────────────────┘
                          ▲
                          │
┌─────────────────────────────────────────────────────┐
│                   Prometheus                         │
└─────────────────────────────────────────────────────┘
                          ▲
                          │
┌──────────────┬──────────┴──────────┬──────────────┐
│   Node-Exporter │  PVE Exporter      │  Node Exporter │
│   (Linux)     │   (Proxmox)        │   (Linux)    │
└──────────────┴─────────────────────┴──────────────┘
```

---

## Workflow

1. Deploy Prometheus stack via Terraform
2. Configure Proxmox API exporter
3. Set up alerting rules in Prometheus
4. Build Grafana dashboards
5. Integrate with notification channels (Telegram/WhatsApp)

---

## Tools & Technologies

- Proxmox VE
- Prometheus
- Grafana
- Terraform
- Alertmanager

---

## Learning Goals

- Cluster monitoring architecture
- Custom metrics collection
- Alert routing and notification
- Infrastructure as Code for observability

---

## Build Milestones

1. [ ] Install and configure Prometheus on Proxmox host
2. [ ] Deploy PVE Exporter with API authentication
3. [ ] Create 3 core Grafana dashboards
4. [ ] Set up Alertmanager with Telegram integration
5. [ ] Write Terraform module for replication

---

*Generated: 2026-09-13*
