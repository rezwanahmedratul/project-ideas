# Self-Hosted Bookmark & Knowledge Manager API

**Category:** Software Development  
**Date:** 2026-08-19  
**Difficulty:** Beginner–Intermediate  

## Overview
A privacy-first, self-hosted REST API + web UI for saving, tagging, and searching bookmarks and notes — your own minimal Pocket + Notion. Everything stays on your server (great for a homelab). Teaches CRUD API design, full-text search, auth, and a clean front-end, without any third-party SaaS.

## Architecture / Structure
```
bookmarks/
├── api/
│   ├── main.py            # FastAPI app
│   ├── models.py          # SQLAlchemy models
│   ├── schemas.py         # Pydantic
│   ├── db.py
│   └── auth.py            # token auth
├── frontend/              # minimal Svelte/Vanilla UI
├── migrations/            # Alembic
├── docker-compose.yml     # api + postgres
└── README.md
```

## Workflow
1. User adds a bookmark (URL + tags + note) via UI or API.
2. Backend fetches the page title/description, stores it, and extracts text for search.
3. Full-text search returns ranked results by tag/keyword.
4. Tag-based filtering and export (markdown/JSON) supported.

## Tools
- Python FastAPI, SQLAlchemy, PostgreSQL (or SQLite)
- Full-text search (Postgres FTS or Whoosh)
- Docker Compose; optional Svelte/Vanilla JS frontend
- Alembic migrations

## Learning Goals
- Design a clean REST API with auth.
- Database modeling + migrations.
- Full-text search implementation.
- Containerizing a multi-component app.

## Build Milestones
1. Scaffold FastAPI + SQLite; implement add/list/get bookmarks.
2. Add tags, full-text search, and Pydantic validation.
3. Add token auth + a simple web UI.
4. Switch to Postgres + Alembic; add page-metadata fetch.
5. Dockerize and add markdown/JSON export + a bookmarklet.
