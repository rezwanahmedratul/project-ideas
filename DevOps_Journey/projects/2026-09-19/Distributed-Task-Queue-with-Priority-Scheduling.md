# Project: Distributed Task Queue with Priority Scheduling

## Overview
Build a distributed task queue system that supports priority scheduling, retry logic, dead letter queues, and real-time monitoring — similar to Celery/RQ but with modern features and better observability.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────┐
│          Distributed Task Queue System              │
├─────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐ │
│  │  Producer   │  │  Broker     │  │  Consumer   │ │
│  │  API        │  │  (Redis/    │  │  Workers    │ │
│  │             │  │   Kafka)    │  │             │ │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘ │
│         │                 │                 │        │
│         └─────────────────┼─────────────────┘        │
│                           ▼                          │
│                 ┌─────────────────┐                 │
│                 │  Scheduler &    │                 │
│                 │  Monitor        │                 │
│                 │  • Priority     │                 │
│                 │  • Retries      │                 │
│                 │  • Dead Letter  │                 │
│                 └─────────────────┘                 │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Client submits task with priority, dependencies, and options
2. Broker routes task to appropriate queue based on priority
3. Workers pick up tasks respecting priority order
4. Task execution with timeout and retry logic
5. Failed tasks move to dead letter queue after max retries
6. Dashboard shows real-time queue status and worker health
7. Metrics collected for scaling and optimization

## Tools
- Python + Redis or Apache Kafka
- Celery or custom implementation
- FastAPI for producer/consumer APIs
- PostgreSQL for task metadata
- Grafana + Prometheus for monitoring
- React or Vue for dashboard

## Learning Goals
- Distributed systems design
- Message queue patterns and protocols
- Priority scheduling algorithms
- Fault tolerance and recovery
- Real-time monitoring and observability

## Build Milestones
1. **Week 1**: Design task schema and broker interface
2. **Week 2**: Implement Redis-based broker
3. **Week 3**: Create worker pool with priority scheduling
4. **Week 4**: Add retry logic and dead letter queue
5. **Week 5**: Build monitoring dashboard
6. **Week 6**: Load testing and optimization
