# Software Dev: Real-Time Collaborative Whiteboard

## Overview
Create a web-based collaborative whiteboard where multiple users can draw, add sticky notes, and arrange diagrams in real-time — with CRDT-based conflict resolution ensuring consistency across all clients.

## Architecture
```
Frontend (Canvas/WebGL) → WebSocket Server
                                 ├── CRDT Engine (Yjs / Automerge)
                                 ├── Document Store (PostgreSQL)
                                 └── Presence Tracker (Redis)
```

## Workflow
1. Users join a room via shared link
2. Each draw/action creates an operation in the CRDT
3. Operations are broadcast via WebSocket to all peers
4. CRDT resolves concurrent edits deterministically
5. Document state persisted to database periodically

## Tools
TypeScript, React, Canvas API, Yjs (CRDT), Socket.IO, PostgreSQL, Redis

## Learning Goals
- Conflict-free Replicated Data Types (CRDTs)
- Real-time collaborative editing patterns
- WebSocket server architecture
- Spatial data management on canvas

## Build Milestones
1. Single-canvas drawing with WebSocket broadcast
2. Integrate Yjs CRDT for conflict resolution
3. Add sticky notes and text elements
4. Implement presence (cursor tracking, user avatars)
5. Add persistent storage and room management
