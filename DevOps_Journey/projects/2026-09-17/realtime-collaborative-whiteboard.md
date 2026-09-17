# Real-Time Collaborative Whiteboard

## Overview
Create a real-time collaborative whiteboard application where multiple users can draw, add shapes, and annotate simultaneously with instant synchronization across all clients.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                     Client Layer                            │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐                    │
│  │ Canvas   │ │ Tools    │ │ User     │                    │
│  │ Renderer │ │ Panel    │ │ List     │                    │
│  └──────────┘ └──────────┘ └──────────┘                    │
└─────────────────────────────────────────────────────────────┘
                          │
                          ▼ WebSocket
┌─────────────────────────────────────────────────────────────┐
│                    Server Layer                             │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │  Operation   │  │  Presence    │  │  State       │      │
│  │  Resolution  │  │  Management  │  │  Storage     │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
```

## Workflow
1. User connects via WebSocket to server
2. Server assigns unique cursor and color
3. Drawing operations captured on client
4. Operations sent to server via WebSocket
5. Server broadcasts to all connected clients
6. Conflict resolution using CRDTs or OT
7. Cursor positions synced in real-time

## Tools
- **TypeScript** / **React** for frontend
- **Canvas API** or **Fabric.js** for rendering
- **Node.js** + **Socket.io** for real-time communication
- **Yjs** or **Automerge** for CRDTs
- **Redis** for presence and state caching
- **PostgreSQL** for board persistence

## Learning Goals
- Real-time collaboration patterns
- WebSocket communication
- Conflict-free replicated data types (CRDTs)
- Canvas rendering optimization

## Build Milestones
1. **Week 1**: Basic canvas with drawing tools
2. **Week 2**: WebSocket server and client connection
3. **Week 3**: Real-time sync of drawings
4. **Week 4**: Implement CRDTs for conflict resolution
5. **Week 5**: Add cursors and presence indicators
6. **Week 6**: Persist boards and add collaboration features
