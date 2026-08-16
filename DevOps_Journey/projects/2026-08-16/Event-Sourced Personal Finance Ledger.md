# Event-Sourced Personal Finance Ledger

## Overview
Build a personal finance tracking system using event sourcing pattern. Every transaction is an immutable event, allowing perfect audit trails and reconstructed account states.

## Architecture
```
Web Interface (React/Vanilla)
    ↓
Event Store (PostgreSQL)
    ↓
Event Sourcing Engine
    ↓
Account Projections
    ↓
Reporting & Analytics
```

## Workflow
1. Design domain events (deposit, withdraw, transfer, categorize)
2. Implement event store with append-only tables
3. Create projection handlers to calculate balances
4. Build API for adding transactions
5. Add reconciliation reports
6. Implement date-range state reconstruction

## Tools
- Python (FastAPI) or Node.js
- PostgreSQL (event store + projections)
- React or HTMX for frontend
- Alembic/Migrate for migrations

## Learning Goals
- Event sourcing pattern fundamentals
- CQRS (Command Query Responsibility Segregation)
- Immutability in financial systems
- Projection and materialized view patterns

## Build Milestones
- [ ] Design event schema
- [ ] Implement append-only event store
- [ ] Build balance projection engine
- [ ] Create transaction API endpoints
- [ ] Add reporting dashboard
- [ ] Implement state-in-time queries

## References
- https://martinfowler.com/eaaDev/EventSourcing.html
- https://docs.microsoft.com/en-us/azure/architecture/patterns/event-sourcing
- https://www.cqrs.nu/Faq/event-sourcing/
