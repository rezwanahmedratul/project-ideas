# Project: Real-Time Collaborative Whiteboard

## Overview
Build a WebSocket-based collaborative whiteboard where multiple users can draw, add sticky notes, and manipulate objects in real-time. Implements conflict resolution and offline synchronization.

## Architecture
```
┌──────────┐    ┌──────────┐    ┌──────────┐
│  Client A │    │  Client B │    │  Client C │
│  (React)  │    │  (React)  │    │  (React)  │
└────┬─────┘    └────┬─────┘    └────┬─────┘
     │ WebSocket      │ WebSocket       │ WebSocket
     └────────────────┼─────────────────┘
                      │
              ┌───────▼────────┐
              │   WebSocket     │
              │   Server        │
              │  (Node/Go)      │
              └───────┬────────┘
                      │
              ┌───────▼────────┐
              │   Operational   │
              │   Transform     │
              │   (OT Engine)   │
              └───────┬────────┘
                      │
              ┌───────▼────────┐
              │   Redis Pub/Sub │
              │   (broadcast)   │
              └────────────────┘
```

## Workflow
1. User opens whiteboard room URL
2. WebSocket connection established
3. All operations (draw, move, delete) sent to server
4. Server applies OT to resolve conflicts
5. Broadcast to all connected clients
6. Operations stored for persistence
7. Offline users replay operations on reconnect

## Tools & Tech Stack
- **React + TypeScript** — Frontend framework
- **Canvas API / Konva.js** — Drawing surface
- **WebSocket** — Real-time communication
- **Go** or **Node.js** — Backend server
- **Redis** — Pub/sub messaging + rate limiting
- **LevelDB/RocksDB** — Operation log persistence
- **Operational Transformation** — Conflict resolution algorithm

## Learning Goals
- WebSocket protocol and messaging patterns
- Real-time collaboration algorithms (OT/CRAAP)
- Canvas manipulation and drawing tools
- State synchronization strategies
- Conflict resolution for concurrent edits
- Offline-first architecture patterns

## Build Milestones
1. [ ] Basic single-user canvas drawing
2. [ ] Add WebSocket server and client connection
3. [ ] Implement real-time cursor sharing
4. [ ] Add drawing primitives (lines, shapes, text)
5. [ ] Implement OT conflict resolution
6. [ ] Add sticky notes and object manipulation
7. [ ] Persist canvas state and history replay

## Reference Links
- [Paper.js — Vector Graphics](https://paperjs.org/)
- [Shared Array Buffer for WebCodecs](https://developer.mozilla.org/en-US/docs/Web/API/SharedArrayBuffer)
- [Operational Transformation Wikipedia](https://en.wikipedia.org/wiki/Operational_transformation)
