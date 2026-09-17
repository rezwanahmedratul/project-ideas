# Rust CLI Tool with Async I/O and Telemetry

## Overview
Build a high-performance command-line toolkit written in Rust that demonstrates async I/O patterns, structured logging, metrics collection, and tracing for observability.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                     CLI Interface                           │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐      │
│  │  File    │ │  Network │ │  Process │ │  System  │      │
│  │  Ops     │ │  Operations│ │Monitor   │ │ Metrics  │      │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘      │
└─────────────────────────────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                   Core Library                              │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Async Runtime (tokio) │ Error Handling │ Config      │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                 Observability Layer                         │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐                 │
│  │  Struct  │  │  Metrics │  │  Tracing │                 │
│  │  Logging │  │  (Prom)  │  │  (OTel)  │                 │
│  └──────────┘  └──────────┘  └──────────┘                 │
└─────────────────────────────────────────────────────────────┘
```

## Workflow
1. Parse CLI arguments with clap
2. Load configuration from file/env
3. Initialize async runtime (tokio)
4. Execute operations with proper error handling
5. Emit structured logs and metrics
6. Export telemetry to collectors
7. Graceful shutdown with signal handling

## Tools
- **Rust** (Edition 2021+)
- **tokio** for async runtime
- **clap** for argument parsing
- **tracing** for structured logging
- **prometheus** for metrics
- **otel** for distributed tracing
- **serde** for serialization

## Learning Goals
- Rust ownership and borrowing patterns
- Async/await in production code
- Structured logging best practices
- Observability instrumentation

## Build Milestones
1. **Week 1**: Set up project structure with Cargo
2. **Week 2**: Implement CLI interface and config loading
3. **Week 3**: Build core async operations
4. **Week 4**: Add logging and metrics
5. **Week 5**: Implement tracing integration
6. **Week 6**: Add tests, benchmarks, and documentation
