# Event-Driven Notifier Service

**Category:** Software Development  
**Date:** 2026-08-19  
Difficulty: Intermediate  

## Overview
A small backend service that consumes events from a message queue (Redis Streams or NATS) and dispatches notifications through pluggable channels (email, Telegram, webhook). It decouples "something happened" from "tell the user," making it reusable across every other project in this list. Teaches event-driven architecture, idempotency, and delivery reliability.

## Architecture / Structure
```
notifier/
├── cmd/server/main.go        # or main.py
├── internal/
│   ├── consumer/             # queue subscription
│   ├── dispatcher/           # route event -> channel
│   ├── channels/
│   │   ├── email.go
│   │   ├── telegram.go
│   │   └── webhook.go
│   └── store/                # delivery state (SQLite/Redis)
├── deploy/docker-compose.yml
├── config.yaml
└── README.md
```

## Workflow
1. Producers publish an event (e.g., `deploy.failed`) to the queue.
2. Consumer pulls events and looks up routing rules.
3. Dispatcher sends via the matched channel(s), tracking delivery state.
4. Failed sends are retried with exponential backoff; duplicates are deduplicated by event ID.

## Tools
- Go (or Python FastAPI), Redis Streams or NATS
- Telegram Bot API, SMTP, or webhook targets
- Docker Compose, SQLite or Redis for state

## Learning Goals
- Event-driven / pub-sub architecture.
- Idempotent processing and at-least-once delivery semantics.
- Pluggable provider pattern.
- Retry/backoff and dead-letter handling.

## Build Milestones
1. Stand up Redis Streams + a producer that emits test events.
2. Build the consumer + a console (stdout) channel end-to-end.
3. Add Telegram and webhook channels.
4. Implement dedupe + retry/backoff + dead-letter.
5. Containerize and write a small demo wiring it to another project's events.
