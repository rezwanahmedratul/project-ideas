# Rust CLI Tool with Async I/O and Telemetry

## Overview
Develop a high-performance CLI utility in Rust demonstrating async I/O patterns, structured logging with OpenTelemetry, and metrics collection. Perfect for learning systems programming and observability.

## Architecture
- **Clap** for argument parsing
- **Tokio** for async runtime
- **OpenTelemetry** for distributed tracing
- **Prometheus** for metrics export
- **Tracing** for structured logging
- **Serde** for serialization/deserialization

## Workflow
1. Parse CLI arguments with Clap
2. Execute async operations (file I/O, network requests)
3. Emit traces to OpenTelemetry collector
4. Export metrics to Prometheus endpoint
5. Log structured events with context
6. Graceful shutdown with cleanup

## Tools
- Rust (2021 edition)
- Cargo workspace for modular structure
- Tokio runtime
- OpenTelemetry SDK and exporters
- Prometheus client library
- Docker for deployment testing

## Learning Goals
- Rust ownership and borrowing concepts
- Async/await patterns and futures
- Systems programming best practices
- Observability (traces, metrics, logs)
- Performance profiling and optimization

## Build Milestones
1. Create basic CLI with argument parsing
2. Implement async file processing pipeline
3. Add OpenTelemetry tracing integration
4. Expose Prometheus metrics endpoint
5. Add structured logging with contexts
6. Profile and optimize performance
7. Package as distributable binary

---
*Generated: 2026-09-18 | Source: AI overnight research engine*
