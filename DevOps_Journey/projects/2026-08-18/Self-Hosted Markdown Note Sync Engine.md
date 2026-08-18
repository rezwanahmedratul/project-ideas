# Self-Hosted Markdown Note Sync Engine

**Category:** Software Development  
**Date:** 2026-08-18  
**Difficulty:** Intermediate

---

## Overview

A conflict-free synchronization engine for Markdown notes across devices, using CRDTs (Conflict-Free Replicated Data Types). Designed as a self-hosted alternative to cloud note sync — perfect for keeping your Obsidian vault in sync between laptop and homelab server without third-party services.

## Architecture / Structure

```
md-sync/
├── cmd/
│   ├── server/           # Sync server (WebSocket)
│   └── daemon/           # Local file watcher client
├── internal/
│   ├── crdt/             # Yjs/RGA CRDT implementation
│   ├── watcher/          # fsnotify file monitoring
│   ├── store/            # BadgerDB / SQLite doc store
│   └── api/              # Sync protocol (WS + REST)
├── proto/
│   └── sync.proto        # gRPC-Web or custom WS protocol
└── web/                  # Optional web editor (Yjs binding)
```

## Workflow

1. **Daemon** watches vault directory via fsnotify
2. On change → compute CRDT diff → push to **Server** over WebSocket
3. **Server** merges updates from all clients (commutative ops)
4. **Server** broadcasts merged state to other connected clients
5. **Client** applies remote updates to local file (atomic write)

## Tools

- **Language:** Go (or Rust)
- **CRDT:** Yjs (automerge alternative), or custom RGA
- **Transport:** WebSocket, Protocol Buffers
- **Storage:** BadgerDB (embedded), or SQLite
- **Watch:** fsnotify
- **Frontend:** CodeMirror 6 + Yjs binding (optional)

## Learning Goals

- CRDT theory: commutative operations, state-based vs. op-based
- Real-time collaborative editing algorithms
- File-system watching and atomic writes
- Designing sync protocols (offline-first)

## Build Milestones

| Milestone | Deliverable | Est. Time |
|-----------|-------------|-----------|
| M1 | CRDT doc model + merge logic | 2 days |
| M2 | WebSocket sync server | 1.5 days |
| M3 | File watcher daemon | 1 day |
| M4 | Offline queue + reconnect | 1 day |
| M5 | Web editor (optional) | 2 days |

---

**Tags:** #crdt #sync #markdown #obsidian #golang #offline-first
