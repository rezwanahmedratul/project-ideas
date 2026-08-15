# Self-Documenting API with AI Summary

**Category:** Combined
**Suggested Date:** 2026-08-15
**Status:** Idea / Not Started

## Overview
A backend service that uses an AI agent to read API schemas, generate human-readable documentation, detect endpoint regressions, and maintain living documentation tied to the source of truth.

## What It Will Do
- Solve a practical problem related to combined.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
self-documenting-api/
├── README.md
├── api/
│   ├── app.py
│   └── routes/
├── docs_gen/
│   ├── openapi_parser.py
│   └── llm_summarizer.py
├── docs/
│   └── generated/
├── tests/
├── schemas/
└── .github/workflows/

## How It Will Work
1. Define the core use case and minimal working workflow.
2. Build the API/automation pipeline first.
3. Add persistence, observability, and error handling.
4. Containerize the application and add CI.
5. Write documentation and create a demo scenario.

## Tools / Tech Stack
OpenAPI/Swagger, FastAPI or Express, Ollama/local LLM, LangChain, Git, pytest, Docker, Redoc/Swagger UI

## Learning Goals
Learn API design standards, OpenAPI spec management, AI-assisted documentation generation, regression detection, and developer experience best practices.

## Build Milestones
- **MVP:** Auto-generate Markdown docs from a FastAPI OpenAPI spec.
- **v1:** Detect when new endpoints break existing documentation contracts.
- **v2:** LLM summarizes each endpoint in plain language with usage examples.
- **Portfolio polish:** Side-by-side doc comparison, regression test suite, live demo API.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
