# Event-Sourced Personal Finance Ledger

## Overview
A personal finance tracker built on event sourcing principles — every transaction is an immutable event, enabling perfect audit trails, temporal queries, and replay capabilities.

## Architecture
```
┌──────────────────────────────────────────────┐
│                Application Layer             │
│  ┌─────────┐  ┌─────────┐  ┌─────────────┐  │
│  │ Commands │  │ Queries │  │ Read Model  │  │
│  └────┬────┘  └────┬────┘  └──────┬──────┘  │
└───────┼────────────┼───────────────┼─────────┘
        │            │               │
   ┌────▼────────────▼───────────────▼─────────┐
   │           Event Store (PostgreSQL)         │
   │  ┌─────────────────────────────────────┐   │
   │  │ Events Table (immutable append-only) │   │
   │  │ - event_id, type, payload, timestamp │   │
   │  │ - aggregate_id, version, stream_pos  │   │
   │  └─────────────────────────────────────┘   │
   └────────────────────────────────────────────┘
                          │
                   ┌──────▼──────┐
                   │ Projections │
                   │ (materialized│
                   │  views)     │
                   └─────────────┘
```

## Workflow
1. User creates transaction → Command issued
2. Event stored immutably in event stream
3. Projection updates account balances
4. Query reads from projection (fast, denormalized)
5. Full history available for audits and reports

## Tools
- **Python** (FastAPI) or **Node.js** (NestJS)
- **PostgreSQL** with JSONB for events
- **Django Events** or custom event store
- **React** or **Svelte** for frontend
- **Plaid API** for bank connection (optional)

## Learning Goals
- Event sourcing pattern
- CQRS (Command Query Responsibility Segregation)
- Projections and materialized views
- Idempotent event handling

## Build Milestones
1. [ ] Event store with PostgreSQL
2. [ ] Transaction command handler
3. [ ] Balance projection (running totals)
4. [ ] Account aggregation view
5. [ ] Time-travel queries (snapshot at date)
6. [ ] Budget tracking and alerts
7. [ ] Bank import via Plaid API
