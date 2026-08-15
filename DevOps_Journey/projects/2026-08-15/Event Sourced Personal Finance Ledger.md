# Event Sourced Personal Finance Ledger

## Overview
A personal finance application using event sourcing pattern to track all financial transactions with full audit trail and replay capabilities.

## Architecture
```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Frontend  │     │   API       │     │  Event      │
│   (React)   │◄───▶│  (Node.js)  │◄───▶│  Store      │
└─────────────┘     └─────────────┘     └─────────────┘
                                        │
                                   ┌───────────┐
                                   │  Snapshot │
                                   │  Store    │
                                   └───────────┘
```

## Workflow
1. **Record**: Every transaction creates an immutable event
2. **Store**: Events persisted in order to event store
3. **Replay**: Rebuild account balance by replaying events
4. **Query**: Read models for fast balance lookups
5. **Audit**: Full history with timestamps and metadata

## Tools
- PostgreSQL or MongoDB for event store
- Node.js / TypeScript for backend
- React or Vue for frontend
- CQRS pattern implementation
- Redis for caching read models

## Learning Goals
- Master event sourcing pattern
- Learn CQRS architecture
- Practice financial application design
- Understand audit trail requirements

## Build Milestones
1. **M1**: Basic event store with transaction events
2. **M2**: Implement event replay for balance calculation
3. **M3**: Add read model projections
4. **M4**: Build frontend with transaction management
5. **M5**: Add reporting and analytics
6. **M6**: Implement multi-account support
