# Rust High-Performance Event Streaming Platform

## Overview

Build a real-time event streaming platform in Rust that handles high-throughput message processing with sub-millisecond latency. This project explores systems programming concepts while implementing producer-consumer patterns suitable for log aggregation, metrics collection, or event sourcing.

## Architecture

```
┌─────────────────────────────────────────────┐
│         Event Streaming Platform             │
│                                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │ Producer │  │ Broker   │  │ Consumer │  │
│  │ API     │  │ (Ring    │  │ API     │  │
│  │ (REST)  │  │ Buffer)  │  │ (WebSocket│  │
│  └──────────┘  └──────────┘  └──────────┘  │
│                                             │
│  ┌─────────────────────────────────────┐    │
│  │ Partition Manager (Rust async)     │    │
│  │ - Zero-copy serialization          │    │
│  │ - Backpressure handling            │    │
│  └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
```

## Workflow

1. **Ingestion**: Accept events via REST API with JSON/MessagePack serialization
2. **Buffering**: Store in lock-free ring buffer with configurable retention
3. **Partitioning**: Distribute events across partitions based on key hashing
4. **Processing**: Consumers pull events with acknowledgment-based delivery
5. **Persistence**: Optional persistent storage using memory-mapped files

## Tools

- Rust with Tokio async runtime
- Serde for serialization
- Axum for HTTP APIs
- WebSockets for real-time consumption
- RocksDB for optional persistence

## Learning Goals

- Master Rust ownership and borrowing in concurrent contexts
- Understand zero-copy deserialization techniques
- Learn ring buffer implementations for low-latency systems
- Practice async Rust patterns with proper backpressure

## Build Milestones

1. **Week 1**: Core ring buffer with basic insert/poll operations
2. **Week 2**: Implement partition management and routing
3. **Week 3**: Add REST API producers and WebSocket consumers
4. **Week 4**: Integrate persistence layer with RocksDB
5. **Week 5**: Benchmark performance and optimize hot paths
