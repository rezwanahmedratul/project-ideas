# Rust-Based System Monitor CLI

## Overview
A high-performance system monitoring CLI written in Rust that provides real-time CPU, memory, disk, network, and process insights with a TUI (terminal user interface). Designed as a lightweight, fast alternative to htop/top with extensible plugin support.

## Architecture / Structure
- **Core**: Rust binary using tokio for async I/O
- **Metrics Collector**: Reads from /proc, sysfs, and netstat APIs
- **TUI Layer**: Ratatui (formerly tui-rs) for terminal rendering
- **Plugin System**: Dynamic loading of metric collectors via trait interface
- **Exporter**: Optional JSON/Prometheus metrics endpoint for remote scraping

## Workflow
1. Launch CLI with default metrics view
2. Each tick, collect CPU usage per-core, RAM, swap, disk I/O, network throughput
3. Render beautiful TUI with color-coded gauges and sortable process table
4. Allow keyboard shortcuts for filtering, sorting, and toggling views
5. Optionally export metrics to Prometheus for long-term storage

## Tools
- Rust + tokio + futures
- Ratatui for TUI rendering
- sysinfo crate for cross-platform system metrics
- Prometheus client for metric export
- Cursive or owo-colors for theming

## Learning Goals
- Systems programming in Rust
- Async I/O with Tokio runtime
- Terminal UI design and ncurses alternatives
- Linux /proc filesystem interfacing

## Build Milestones
1. Week 1: Basic CPU + memory metrics from /proc/stat and /proc/meminfo
2. Week 2: Process table with sorting and filtering
3. Week 3: Disk I/O and network throughput graphs
4. Week 4: Ratatui TUI with themes and keyboard navigation
5. Week 5: Plugin system for extensible metric collectors
6. Week 6: Prometheus exporter and systemd service integration
