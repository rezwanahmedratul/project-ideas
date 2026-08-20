# Project: Event-Sourced Personal Finance Ledger

**Category:** Software Development  
**Date:** 2026-08-20

---

## Overview

Build an event-sourced personal finance application that tracks every transaction as an immutable event. Provides complete audit trail, ability to reconstruct any historical state, and powerful replay capabilities for financial analysis.

---

## What It Does

- Record income, expenses, transfers as immutable events
- Reconstruct account balances at any point in time
- Generate reports: net worth, spending categories, trends
- Support for multi-currency with automatic conversion
- Audit trail for all changes (who, what, when)

---

## Architecture/Structure

```
finance-ledger/
├── src/
│   ├── domain/
│   │   ├── events.py      # Event types (Deposit, Withdrawal, Transfer)
│   │   ├── account.py     # Account aggregate root
│   │   └── ledger.py      # Event store
│   ├── application/
│   │   ├── services.py    # Use cases
│   │   └── commands.py    # Command handlers
│   └── infrastructure/
│       ├── db.py          # PostgreSQL with JSONB events
│       └── api.py         # FastAPI endpoints
├── tests/
│   └── test_ledger.py
└── docker-compose.yml
```

---

## Workflow

1. **User creates transaction** → Command validated and event created
2. **Event appended** → Stored in event store with timestamp and ID
3. **Projection updated** → Account balance projection recalculated
4. **Response returned** → Confirmation with new balance
5. **History query** → Replay events to reconstruct any historical state

---

## Tools/Tech Stack

| Component | Technology |
|-----------|------------|
| Language | Python 3.11+ |
| Framework | FastAPI |
| Database | PostgreSQL (JSONB for events) |
| Event Store | Custom implementation or EventStoreDB |
| Projections | Redis for current balances |
| Frontend | React or simple HTML/CSS |
| Testing | pytest, factory-boy |

---

## Learning Goals

- Event sourcing fundamentals and patterns
- CQRS (Command Query Responsibility Segregation)
- Immutability and audit trails
- Projection and materialized view design
- Financial data modeling best practices

---

## Build Milestones

1. **Week 1:** Core event types and event store
2. **Week 2:** Account aggregate with balance calculation
3. **Week 3:** API layer with CRUD operations
4. **Week 4:** Historical state reconstruction
5. **Week 5:** Reporting and analytics
6. **Week 6:** Multi-currency support and frontend

---

## Stretch Goals

- Integration with bank APIs for automatic transaction import
- Machine learning for spending pattern prediction
- Budget planning with alerts
- Multi-user support with role-based access
