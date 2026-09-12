# Prometheus Custom Exporters Library

## Overview
Build a collection of Prometheus exporters for common services (Redis, PostgreSQL, Nginx, custom apps) with standardized metrics and alerting rules.

## Architecture
- Exporter framework: Python Prometheus client
- Metrics registry: Standardized metric naming
- Alert rules: Pre-configured Alertmanager rules
- Documentation: Metrics reference and dashboards

## Workflow
1. Clone exporter library
2. Configure service connection parameters
3. Deploy exporter alongside target service
4. Prometheus scrapes metrics endpoint
5. Alertmanager triggers notifications

## Tools
- Python, Prometheus client, Alertmanager, Grafana

## Learning Goals
- Prometheus metrics design
- Exporter development patterns
- Alerting rule best practices
- Monitoring system architecture

## Build Milestones
1. Exporter base class and utilities
2. Redis exporter with key metrics
3. PostgreSQL exporter with query metrics
4. Nginx exporter with request metrics
5. Dashboard templates and alerts
