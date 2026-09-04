# WebAssembly Microservices Communication Framework

## Overview
A lightweight framework for building WebAssembly-based microservices that communicate via gRPC over WASI, enabling language-agnostic service composition with near-native performance.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────────┐
│            WASM Microservices Framework                 │
├─────────────┬──────────────┬──────────────┬─────────────┤
│  WASI       │  gRPC        │  Service     │  Runtime    │
│  Transport  │  Codegen     │  Registry    │  Manager    │
├─────────────┴──────────────┴──────────────┴─────────────┤
│              WASM Plugins (Rust, Go, TypeScript)         │
└─────────────────────────────────────────────────────────┘
```

## Workflow
1. Developer writes service in any compiled language targeting WASM
2. Framework generates gRPC bindings from protobuf definitions
3. Services register with central registry on startup
4. Runtime manager loads and isolates WASM modules
5. Cross-service calls use WASI-io for transport

## Tools
- Rust (wasm32-unknown-unknown target)
- WASI SDK
- gRPC with WASI transport plugin
- wasmtime for runtime
- Protocol Buffers for IDL

## Learning Goals
- WebAssembly system interfaces (WASI)
- gRPC service composition
- Cross-language interop patterns
- Microkernel architecture design

## Build Milestones
1. **M1**: Single WASM service with HTTP endpoint
2. **M2**: gRPC code generation for Rust services
3. **M3**: Service registry with discovery
4. **M4**: Cross-service gRPC calls
5. **M5**: Multi-language support (Go, TypeScript plugins)
6. **M6**: Production runtime with health checks and scaling
