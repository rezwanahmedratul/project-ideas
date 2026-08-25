# Project: Rust Web Service with OpenTelemetry Tracing

## Overview
Build a production-ready Rust web service (Actix-web) that implements distributed tracing using OpenTelemetry. Instrument HTTP requests, database queries, and inter-service calls, then export traces to Jaeger for visualization and debugging.

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│  Client (curl / browser)                           │
│       │                                              │
│       ▼                                              │
│  ┌─────────────────────────────────────────────┐    │
│  │  Rust Service (Actix-web)                    │    │
│  │  ├── main.rs         (tracing OTel init)     │    │
│  │  ├── handlers/     (HTTP route handlers)     │
│  │  ├── db/           (PostgreSQL queries)      │
│  │  └── middleware/   (trace context propagation)│
│  └──────┬──────────────────┬────────────────────┘    │
│         │                  │                         │
│    ┌────▼────┐      ┌──────▼─────┐                  │
│    │ PostgreSQL│      │ Redis Cache │                  │
│    └────┬────┘      └────────────┘                  │
├─────────────────────────────────────────────────────┤
│  Observability                                     │
│  ├── Jaeger (trace collector + UI)                  │
│  ├── OTLP Collector (optional aggregation)          │
│  └── Grafana (visualize trace data)                 │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Scaffold a new Rust project with `cargo new`; add Actix-web, `opentelemetry`, `tracing-opentelemetry` crates
2. Configure OpenTelemetry SDK: tracing provider, batch span processor, OTLP exporter
3. Add middleware to extract/inject trace context from HTTP headers (W3C tracecontext)
4. Instrument the main handler: create named spans for each logical operation
5. Add DB instrumentation with `tracing` crate; wrap SQL queries with spans
6. Simulate an outgoing HTTP call (to another service) with automatic context propagation
7. Deploy Jaeger all-in-one via Docker Compose alongside the Rust service
8. Verify traces appear in Jaeger UI with correct parent-child relationships

## Tools
- **Rust** (latest stable, 2024 edition)
- **Actix-web** (web framework)
- **OpenTelemetry Rust** (tracing SDK + OTLP exporter)
- **Jaeger** (distributed tracing backend)
- **Docker Compose** (local observability stack)
- **tracing** + **tracing-subscriber** (structured logging)

## Learning Goals
- Rust async/await patterns with Actix-web
- OpenTelemetry concepts: spans, trace context, propagators
- Structured logging with the `tracing` crate
- Trace context propagation across HTTP boundaries (Bearer/W3C)
- Database query instrumentation in Rust
- Deploying observability tooling with Docker Compose

## Build Milestones
1. [ ] Create Rust project; add Actix-web, otel, tracing dependencies
2. [ ] Initialize OTel tracing provider in `main()`
3. [ ] Implement health check endpoint; verify trace appears in Jaeger
4. [ ] Add user CRUD endpoints; instrument each handler with named spans
5. [ ] Connect PostgreSQL; wrap queries with `tracing::instrument`
6. [ ] Add HTTP client middleware; propagate trace context to downstream calls
7. [ ] Switch to BatchSpanProcessor for efficient export
8. [ ] Create docker-compose.yml with Rust service + Jaeger + PostgreSQL

## References
- https://opentelemetry.io/docs/languages/rust/
- https://github.com/open-telemetry/opentelemetry-rust
