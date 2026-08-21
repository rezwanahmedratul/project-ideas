# Rust CLI Task Automation Framework

## Overview
A plugin-based CLI framework built in Rust for automating repetitive development and DevOps tasks, with hot-reloadable plugins and a rich extension ecosystem.

## Architecture
```
┌─────────────────────────────────────────┐
│           CLI Binary (Rust)             │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐   │
│  │ Core    │ │ Plugin  │ │ Plugin  │   │
│  │ Engine  │ │ Loader  │ │ Runner  │   │
│  └────┬────┘ └────┬────┘ └────┬────┘   │
│       │           │           │         │
│       └───────────┼───────────┘         │
│                   ▼                     │
│          ┌─────────────────┐            │
│          │  Plugin Registry│            │
│          │  (Config + Docs)│            │
│          └─────────────────┘            │
└─────────────────────────────────────────┘
```

## Workflow
1. User defines tasks in YAML/JSON config
2. CLI parses args and resolves task dependencies
3. Plugin system executes pre/post hooks
4. Results logged with timing and exit codes
5. Plugins can be written in Rust or called as shell commands

## Tools
- **Rust** (clap, serde, tokio for async)
- **Cargo workspace** for plugin isolation
- **Dunce** for cross-platform paths
- **Rustyline** for interactive mode

## Learning Goals
- Rust ownership and concurrency patterns
- Plugin architecture design
- CLI best practices (subcommands, flags, autocomplete)
- Cross-platform compatibility

## Build Milestones
1. [ ] Core CLI with basic task execution
2. [ ] Plugin loader with dynamic loading
3. [ ] Task dependency graph resolution
4. [ ] Config validation and schema
5. [ ] Rich logging and progress indicators
6. [ ] Shell completions (bash/zsh/fish)
7. [ ] Plugin marketplace (GitHub registry)
