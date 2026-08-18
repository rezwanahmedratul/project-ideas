# Event-Sourced Task Tracker with CQRS

**Category:** Software Development  
**Date:** 2026-08-18  
**Difficulty:** Intermediate

---

## Overview

A personal task/todo tracker built on Event Sourcing + CQRS patterns. Every state change is an immutable event; read models are rebuilt from the event log. Demonstrates production-grade architecture for a simple domain. Includes a web UI and REST API.

## Architecture / Structure

```
task-tracker-es/
├── cmd/
│   ├── api/              # Command + Query HTTP servers
│   └── projector/        # Rebuilds read models from events
├── internal/
│   ├── domain/           # Task aggregate, events, commands
│   ├── eventstore/       # Append-only store (SQLite/Postgres)
│   ├── projection/       # Read models (today, overdue, by-tag)
│   └── http/             # Handlers (commands + queries)
├── web/                  # Svelte/HTMX frontend
├── migrations/           # Schema for event store + projections
└── docker-compose.yml
```

## Workflow

1. **Command** (e.g., `CreateTask`, `CompleteTask`) validated by aggregate
2. **Event** appended to event store (immutable, versioned)
3. **Projector** consumes event → updates read models
4. **Query** reads from projection (fast, denormalized)
5. **Replay** rebuilds all projections from event log on schema change

## Tools

- **Backend:** Go (or Rust) with standard net/http
- **Event Store:** PostgreSQL (JSONB) or SQLite
- **Frontend:** SvelteKit or HTMX + Alpine.js
- **Messaging:** In-process event bus (or NATS for distributed)
- **Testing:** Property-based tests for aggregate invariants

## Learning Goals

- Event Sourcing vs. CRUD trade-offs
- CQRS separation of write/read models
- Event versioning and schema evolution
- Replay/projection rebuild strategies

## Build Milestones

| Milestone | Deliverable | Est. Time |
|-----------|-------------|-----------|
| M1 | Event store + aggregate (commands) | 1.5 days |
| M2 | Projection read models | 1 day |
| M3 | REST API (commands + queries) | 1 day |
| M4 | Web UI (create/complete/list) | 2 days |
| M5 | Replay tool + tests | 1 day |

---

**Tags:** #event-sourcing #cqrs #go #architecture #backend
