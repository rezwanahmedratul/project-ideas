# Project: Rust CLI Tool with Async I/O

## Overview
Build a production-quality CLI tool in Rust that demonstrates async I/O patterns, clap argument parsing, error handling, and cross-platform compilation. Includes tests, documentation, and GitHub Actions CI.

## Architecture
```
┌─────────────────────────────────────────────────┐
│               CLI Binary                        │
├─────────────────────────────────────────────────┤
│  CLI Args (clap)                                │
│       │                                         │
│       ▼                                         │
│  Command Handlers                               │
│  ├── fetch.rs (HTTP requests)                  │
│  ├── parse.rs (data processing)                │
│  └── output.rs (JSON/text formatting)          │
│       │                                         │
│       ▼                                         │
│  Business Logic                                 │
│  ├── Error types (thiserror)                   │
│  ├── Result chains (anyhow)                    │
│  └── Config (serde + toml)                     │
└─────────────────────────────────────────────────┘
         │
    ┌────┴────┐
    ▼         ▼
Async Runtime  Cross-compile
(tokio)        (cross, cargo-zigbuild)
```

## Workflow
1. Define command structure with clap (subcommands, flags, options)
2. Implement async handlers using tokio runtime
3. Handle errors with thiserror + anyhow pattern
4. Write unit tests and integration tests
5. Cross-compile for macOS/Linux/Windows
6. Publish to crates.io and GitHub releases

## Tools & Tech Stack
- **Rust 2024 Edition** — Language
- **Tokio** — Async runtime
- **Clap v4** — Argument parsing with derive API
- **Reqwest + Hyper** — HTTP client
- **Serde** — Serialization/deserialization
- **Thiserror** — Error type definitions
- **Anyhow** — Error context chaining
- **Cross** — Cross-compilation toolchain
- **cargo-zigbuild** — Optimized cross-compilation

## Learning Goals
- Rust ownership and borrowing in CLI contexts
- Async/await patterns with Tokio
- Error handling idioms (thiserror vs anyhow)
- Cross-platform binary distribution
- GitHub Actions for Rust CI/CD
- Crate publishing workflow

## Build Milestones
1. [ ] Scaffold project with cargo init
2. [ ] Implement main command structure (clap)
3. [ ] Add async HTTP fetching logic
4. [ ] Implement structured JSON output
5. [ ] Add comprehensive test suite
6. [ ] Set up CI with GitHub Actions (lint, test, build)
7. [ ] Publish first release with GitHub artifacts

## Example Use Case
A CLI tool that fetches GitHub repo stats (stars, forks, recent commits) and displays formatted reports. Can be extended to monitor multiple repos and send alerts.

## Reference Links
- [The Rust CLI Book](https://rust-cli.github.io/book/)
- [Tokio Documentation](https://tokio.rs/tokio/tutorial)
- [Clap Derive Guide](https://docs.rs/clap/latest/clap/_derive/)
- [Cross-Compilation Guide](https://github.com/cross-rs/cross)
