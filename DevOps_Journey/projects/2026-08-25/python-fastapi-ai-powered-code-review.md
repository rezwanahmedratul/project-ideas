# Project: Python FastAPI Service with AI-Powered Code Review

## Overview
Build a FastAPI backend service that accepts code diffs via REST API and uses an LLM (via API or local model) to perform automated code reviews. Return structured feedback with severity ratings, suggested fixes, and explanations. Includes caching, rate limiting, and evaluation metrics.

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│  Client Applications                                │
│  ┌──────────────┐  ┌──────────────┐                │
│  │  GitHub PR   │  │  CLI (curl)  │                │
│  └──────┬───────┘  └──────┬───────┘                │
│         │                  │                        │
│         └────────┬─────────┘                        │
│                  ▼                                   │
│  ┌──────────────────────────────────────────────┐   │
│  │  FastAPI Service (port 8000)                  │   │
│  │  ├── /review          POST /review            │   │
│  │  ├── /health          GET  /health            │   │
│  │  ├── /stats           GET  /stats             │   │
│  │  └── /models          GET  /models            │   │
│  │      Routes, Schemas, Services                │   │
│  │      └── ReviewService (calls LLM)            │   │
│  └──────┬───────────────────────────────────────┘   │
│         │                                           │
│  ┌──────▼───────┐  ┌──────────────┐                 │
│  │  Redis Cache │  │  LLM Provider│                 │
│  │  (diff hash) │  │  (OpenAI/    │                 │
│  │              │  │   Anthropic/ │                 │
│  │              │  │   local)     │                 │
│  └──────────────┘  └──────────────┘                 │
├─────────────────────────────────────────────────────┤
│  Evaluation Dataset (JSONL with ground-truth labels)│
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Scaffold FastAPI project with `uvicorn`, `pydantic`, `redis`
2. Define request/response schemas: `ReviewRequest(diff, language)`, `ReviewResponse(feedback[])`
3. Implement `/review` endpoint: accept unified diff text, call LLM with system prompt for code review criteria
4. Add Redis caching: if same diff hash requested, return cached result instantly
5. Implement rate limiting with `slowapi` (10 requests/min per IP)
6. Add evaluation harness: load a dataset of reviewed diffs + human labels; compute precision/recall
7. Add `/stats` endpoint exposing aggregate metrics (latency percentiles, accuracy over time)
8. Containerize with multi-stage Dockerfile; deploy locally

## Tools
- **Python 3.12** + **FastAPI** + **Uvicorn**
- **Pydantic** (request/response models)
- **Redis** (caching layer)
- **SlowAPI** (rate limiting)
- **OpenAI / Anthropic / Ollama** (LLM provider)
- **Docker** + **Docker Compose** (local deployment)

## Learning Goals
- FastAPI dependency injection and lifecycle events
- Pydantic v2 models and request validation
- Redis caching patterns (TTL-based, hash lookup)
- Rate limiting implementation in FastAPI
- Structured LLM prompting for code review tasks
- Building evaluation metrics for AI-powered tools

## Build Milestones
1. [ ] Scaffold FastAPI app; define models and `/health` endpoint
2. [ ] Implement `/review` endpoint with OpenAI API call
3. [ ] Add Redis caching by diff content hash
4. [ ] Add rate limiting middleware (slowapi)
5. [ ] Create evaluation dataset; implement accuracy scoring
6. [ ] Add `/stats` endpoint with latency and metric aggregates
7. [ ] Write multi-stage Dockerfile; test local deployment
8. [ ] Add Swagger docs exploration with `--reload` flag

## References
- https://fastapi.tiangolo.com/
- https://python.langchain.com/docs/integrations/providers/openai/
