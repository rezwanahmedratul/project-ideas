# WebAssembly Microservices Gateway with gRPC

## Overview
Build a high-performance API gateway using WebAssembly modules compiled from Rust, enabling dynamic plugin loading and sub-millisecond request routing with gRPC support.

## Architecture
```
┌─────────────────────────────────────────┐
│     Wasm Microservices Gateway          │
├─────────────────────────────────────────┤
│  Request Router                         │
│  ├─ Host header matching                │
│  ├─ Path-based routing                  │
│  └─ gRPC service discovery              │
├─────────────────────────────────────────┤
│  Wasm Runtime (Wasmtime)                │
│  ├─ Plugin module A (auth)              │
│  ├─ Plugin module B (rate limit)        │
│  └─ Plugin module C (transform)         │
├─────────────────────────────────────────┤
│  Upstream Services                      │
│  ├─ gRPC service 1                      │
│  ├─ gRPC service 2                      │
│  └─ REST service 3                      │
└─────────────────────────────────────────┘
```

## Workflow
1. Request arrives at gateway
2. Route lookup based on headers/path
3. Load and execute Wasm plugins in isolation
4. Transform request, call upstream gRPC
5. Transform response and return

## Tools
- Rust + Wasmtime
- gRPC + protoc
- Tower (HTTP middleware framework)
- Prometheus for metrics

## Learning Goals
- WebAssembly compilation from Rust
- Microgateway architecture
- gRPC-Web interoperability
- Plugin lifecycle management

## Build Milestones
- [ ] Week 1: Basic HTTP router
- [ ] Week 2: Wasmtime integration
- [ ] Week 3: Plugin API design
- [ ] Week 4: gRPC passthrough
- [ ] Week 5: Plugin marketplace
- [ ] Week 6: Performance testing
