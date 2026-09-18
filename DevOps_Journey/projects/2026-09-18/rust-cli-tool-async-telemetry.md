# Rust CLI Tool with Async I/O and Telemetry

## Overview
Develop a high-performance command-line tool in Rust demonstrating async I/O patterns, structured logging, metrics collection, and distributed tracing capabilities.

## Architecture
- **Tokio** runtime for async operations
- **Tracing** for structured logging and distributed traces
- **Metrics** crate for application counters/gauges/histograms
- **Clap** for argument parsing
- **Serde** for serialization/deserialization

## Workflow
1. Parse CLI arguments efficiently
2. Execute async operations with backpressure handling
3. Emit structured logs with correlation IDs
4. Collect and export metrics to Prometheus
5. Generate distributed traces for Jaeger/Tempo

## Tools
- Rust programming language
- Tokio async runtime
- Tracing ecosystem
- Prometheus client library
- OpenTelemetry for tracing

## Learning Goals
- Rust async/await patterns
- Production-grade logging and monitoring
- Distributed systems observability
- High-performance CLI design

## Build Milestones
1. Basic CLI skeleton with Clap
2. Implement async I/O operations
3. Add structured logging with Tracing
4. Integrate metrics collection
5. Add distributed tracing support

---

*Generated: 2026-09-18 | Source: AI overnight research engine*
