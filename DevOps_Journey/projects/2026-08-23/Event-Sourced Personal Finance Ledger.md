# Event-Sourced Personal Finance Ledger

**Category:** Software Development  
**Date:** 2026-08-23

---

## Overview

Build a personal finance application using event sourcing and CQRS patterns. Every financial transaction is stored as an immutable event, enabling perfect audit trails, temporal queries ("what was my balance on March 15?"), and easy reconciliation. Great for learning modern software architecture patterns.

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│           Event-Sourced Finance Ledger               │
│                                                     │
│  ┌─────────┐    ┌─────────────┐    ┌────────────┐  │
│  │  UI     │◀──▶│  Read Model │◀──▶│  Query DB  │  │
│  │(React/  │    │  ( projections)│   │  (SQLite)  │  │
│  │ Next.js)│    └─────────────┘    └────────────┘  │
│  └────┬────┘                                         │
│       │                                              │
│  ┌────▼────┐    ┌─────────────┐    ┌────────────┐  │
│  │ Commands│───▶│  Command     │───▶│  Event     │  │
│  │ Handler │    │  Validation  │    │  Store     │  │
│  └─────────┘    └─────────────┘    │  (PostgreSQL│  │
│                                    │   + JSONB) │  │
│                                    └─────┬──────┘  │
│                                          │          │
│                                    ┌─────▼──────┐  │
│                                    │  Projection │  │
│                                    │  Builders   │  │
│                                    └─────────────┘  │
└─────────────────────────────────────────────────────┘
```

---

## Workflow

1. **User** creates a command (e.g., "Add expense $50 at grocery")
2. **Validation** checks rules (balance sufficient, category valid)
3. **Event** is appended to append-only store
4. **Projection** rebuilds read model from events
5. **Query** returns current state to UI
6. **History** available by replaying events

---

## Tools & Stack

| Component | Technology |
|-----------|-----------|
| Backend | Python (FastAPI) or Node.js (NestJS) |
| Event Store | PostgreSQL with JSONB or EventStoreDB |
| Read Model | Materialized views or Redis |
| Frontend | React/Next.js or Vue/Nuxt |
| Testing | pytest/jest with event replay |
| Deployment | Docker Compose |

---

## Learning Goals

- Event sourcing fundamentals
- CQRS pattern implementation
- Projection/rebuilder design
- Idempotency and deduplication
- Snapshot optimization
- Temporal query patterns

---

## Build Milestones

| Phase | Deliverable | Timeline |
|-------|-------------|----------|
| 1. Domain Model | Event types, value objects | Week 1 |
| 2. Event Store | Append-only persistence layer | Week 2 |
| 3. Commands | CRUD operations with validation | Week 3 |
| 4. Projections | Balance, transaction lists | Week 4 |
| 5. API | REST/GraphQL endpoints | Week 5 |
| 6. UI | Dashboard with charts | Week 6 |
| 7. Advanced | Time-travel queries, reconciliation | Week 7 |

---

## Reference Resources

- [Event Sourcing Fundamentals](https://docs.microsoft.com/en-us/azure/architecture/patterns/event-sourcing)
- [CQRS Pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/cqrs)
- [EventStoreDB Documentation](https://eventstore.com/docs/)
