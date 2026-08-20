# Rust Log Shipper CLI

**Category:** Software Development  
**Date:** 2026-08-19  
**Difficulty:** Intermediate  

## Overview
A fast, single-binary CLI written in Rust that tails, parses, filters, and ships logs to multiple destinations (stdout, file, Loki, or a webhook). Think a tiny `vector`/`fluentd` you fully understand and can extend. It teaches systems-level Rust: file I/O, async, parsing, and pluggable sinks.

## Architecture / Structure
```
logshipper/
├── Cargo.toml
├── src/
│   ├── main.rs
│   ├── tail.rs        # file tailing (notify/watch)
│   ├── parse.rs       # regex / JSON line parsing
│   ├── filter.rs      # include/exclude rules
│   └── sinks/
│       ├── stdout.rs
│       ├── file.rs
│       ├── loki.rs
│       └── webhook.rs
├── config.toml
└── tests/
```

## Workflow
1. User runs `logshipper --config config.toml`.
2. Watches one or more files (via `notify`).
3. Parses each line (JSON or regex capture groups).
4. Applies filters (level, contains, exclude).
5. Forwards matched lines to configured sinks concurrently.

## Tools
- Rust (cargo), `tokio` (async), `serde`/`toml`, `notify`, `reqwest`, `clap`

## Learning Goals
- Real-world Rust project structure and error handling (`anyhow`/`thiserror`).
- Async I/O and concurrency with Tokio.
- Trait-based extensibility (the `Sink` trait).
- CLI design with `clap` + TOML config.

## Build Milestones
1. Scaffold the crate; implement file tailing to stdout.
2. Add JSON/regex parsing + a level filter.
3. Implement the `Sink` trait and a file sink.
4. Add Loki and webhook sinks with async dispatch.
5. Write integration tests + a `--dry-run` mode and publish a release binary.
