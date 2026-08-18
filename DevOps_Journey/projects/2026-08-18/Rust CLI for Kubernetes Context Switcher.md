# Rust CLI for Kubernetes Context Switcher

**Category:** Software Development  
**Date:** 2026-08-18  
**Difficulty:** Beginner-Intermediate

---

## Overview

A blazing-fast `kubectx`/`kubens` alternative written in Rust that lets you switch between Kubernetes contexts and namespaces with fuzzy search, shell completion, and a TUI picker. Targets homelab users juggling multiple Proxmox-hosted clusters.

## Architecture / Structure

```
kctx-rs/
├── src/
│   ├── main.rs           # CLI entry, clap derive
│   ├── kubeconfig.rs     # Parse ~/.kube/config YAML
│   ├── fuzzy.rs          # Fuzzy match contexts/namespaces
│   ├── tui.rs            # ratatui picker
│   └── shell.rs          # Completion scripts (bash/zsh/fish)
├── tests/
│   └── integration.rs
├── benches/
│   └── switch.rs         # Criterion benchmarks
└── completions/          # Generated completion files
```

## Workflow

1. Parse `~/.kube/config` → list contexts + current
2. `kctx <query>` → fuzzy match → set `current-context`
3. `kctx -i` → open TUI, arrow keys + fuzzy filter
4. Generate shell completion on install
5. Benchmark vs. original Go `kubectx`

## Tools

- **Language:** Rust (edition 2021)
- **CLI:** clap, clap_complete
- **TUI:** ratatui, crossterm
- **Fuzzy:** fuzzy-matcher or skim
- **Config:** serde_yaml
- **Bench:** criterion

## Learning Goals

- Rust CLI patterns with clap derive
- YAML parsing with serde
- Building terminal UIs with ratatui
- Writing criterion benchmarks, comparing against baseline

## Build Milestones

| Milestone | Deliverable | Est. Time |
|-----------|-------------|-----------|
| M1 | Parse kubeconfig, list contexts | 0.5 day |
| M2 | Switch context + fuzzy search | 1 day |
| M3 | TUI picker with ratatui | 1.5 days |
| M4 | Shell completions | 0.5 day |
| M5 | Criterion bench vs kubectx | 0.5 day |

---

**Tags:** #rust #cli #kubernetes #tui #homelab
