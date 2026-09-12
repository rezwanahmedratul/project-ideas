# Rust Microservice Template with Observability

## Overview
Build a production-ready Rust microservice template featuring structured logging, metrics, tracing, and health checks following 12-factor app principles.

## Architecture
- Service framework: Axum or Actix-web
- Logging: Tracing with JSON output
- Metrics: Prometheus exporter
- Health: Readiness and liveness probes
- Configuration: Typed config with validation

## Workflow
1. Define service interface and configuration
2. Implement request handlers with tracing
3. Add metrics collection points
4. Configure health check endpoints
5. Containerize with multi-stage builds

## Tools
- Rust, Axum/Actix, Prometheus, Grafana, Docker

## Learning Goals
- Rust async programming patterns
- Production observability implementation
- Containerization best practices
- API design principles

## Build Milestones
1. Project scaffolding with Cargo
2. HTTP server with request handling
3. Structured logging implementation
4. Metrics and tracing integration
5. Docker packaging and documentation
