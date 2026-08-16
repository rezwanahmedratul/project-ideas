# Offline-First Study Planner with Sync

## Overview
Create a study planning application that works entirely offline first, with optional cloud sync when connectivity is available. Uses SQLite locally and syncs conflict-free with CRDTs.

## Architecture
```
Mobile/Desktop App (PWA)
    ↓
SQLite Database (local-first)
    ↓
CRDT Sync Engine (Automerge/Yjs)
    ↓
Sync Server (optional)
```

## Workflow
1. Build PWA with service worker for offline caching
2. Implement SQLite schema for courses/schedules/tasks
3. Add CRUD operations with optimistic updates
4. Integrate Automerge for CRDT-based sync
5. Create sync server for multi-device support
6. Handle conflicts gracefully

## Tools
- JavaScript/TypeScript (PReact or Vanilla)
- SQLite (sql.js for browser)
- Automerge (CRDT library)
- IndexedDB for persistence
- Service Workers for offline

## Learning Goals
- Local-first software architecture
- Conflict-free Replicated Data Types (CRDTs)
- Progressive Web App development
- Offline data synchronization patterns

## Build Milestones
- [ ] Scaffold PWA with service worker
- [ ] Create SQLite schema for study data
- [ ] Implement local CRUD operations
- [ ] Integrate Automerge for sync
- [ ] Build sync server backend
- [ ] Add conflict resolution UI

## References
- https://automerge.org/
- https://crdt.tech/
- https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps
