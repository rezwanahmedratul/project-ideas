# Rust High-Performance Event Streaming Platform

## Overview
Design and implement a lightweight event streaming platform in Rust, competing with Kafka but optimized for embedded and edge deployments with minimal resource footprint.

## Architecture
```
┌─────────────────────────────────────────┐
│         Event Streaming Platform        │
├─────────────────────────────────────────┤
│  Producer API                           │
│  ├─ Async publish (tokio)               │
│  ├─ Batch optimization                  │
│  └─ Retry with backoff                  │
├─────────────────────────────────────────┤
│  Broker Layer                           │
│  ├─ Log-segment storage (mmap)          │
│  ├─ Partition management                │
│  └─ Replication protocol                │
├─────────────────────────────────────────┤
│  Consumer API                           │
│  ├─ Offset tracking                     │
│  ├─ Exactly-once semantics              │
│  └─ Lag monitoring                      │
└─────────────────────────────────────────┘
```

## Workflow
1. Define topic schema and partition strategy
2. Producers publish messages with headers
3. Broker persists to append-only log segments
4. Consumers subscribe with offset management
5. Automatic compaction for retention policy

## Tools
- Rust (tokio, serde, bytes)
- RocksDB or LMDB for storage
- gRPC for inter-broker communication
- Prometheus metrics export

## Learning Goals
- Systems programming in Rust
- Concurrency patterns (async/await)
- Storage engine design
- Network protocol implementation

## Build Milestones
- [ ] Week 1: Core message types and serialization
- [ ] Week 2: Single-node broker with persistence
- [ ] Week 3: Producer and consumer APIs
- [ ] Week 4: Partition management
- [ ] Week 5: Replication protocol
- [ ] Week 6: Performance benchmarking
