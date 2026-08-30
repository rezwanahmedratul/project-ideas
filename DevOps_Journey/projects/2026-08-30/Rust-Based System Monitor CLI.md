# Rust-Based System Monitor CLI

## Overview
A high-performance command-line system monitor written in Rust that provides real-time CPU, memory, disk, network, and process visualization. Designed for low overhead and beautiful terminal output with configurable themes.

## Architecture / Structure
- **Data Collector**: Async Rust tasks reading /proc filesystem and netlink sockets
- **Filter Engine**: User-configurable thresholds for alerting
- **Renderer**: Crossterm-based terminal UI with refresh rates up to 10Hz
- **Exporter**: Optional Prometheus metrics endpoint for external scraping
- **Config Manager**: YAML/JSON config with hot-reload support

## Workflow
1. Launch monitor binary with optional config file
2. Spawn async collect tasks for each subsystem
3. Update circular buffer with latest metric snapshots
4. Render tui with user-defined panels (tree/grid/list views)
5. Export data points to Prometheus endpoint if enabled
6. Send desktop notifications for threshold breaches

## Tools
- Rust (async-std or tokio runtime)
- Crossterm for terminal rendering
- prometheus-client for metrics export
- notify for config file watching
- serde for serialization

## Learning Goals
- Systems programming in Rust
- Linux proc filesystem and netlink interfaces
- Asynchronous Rust patterns
- Terminal user interface design
- Performance optimization for real-time data

## Build Milestones
1. Week 1: Cargo project setup with basic CPU/memory display
2. Week 2: Procfs reader implementation for processes
3. Week 3: Network interface monitoring via netlink
4. Week 4: Disk IOPS and throughput calculation
5. Week 5: Full TUI with multiple panels and color themes
6. Week 6: Prometheus exporter and notification alerts
