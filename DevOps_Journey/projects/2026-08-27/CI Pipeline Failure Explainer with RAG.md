# CI Pipeline Failure Explainer with RAG

**Date:** 2026-08-27
**Category:** Combined (DevOps + AI)
**Tags:** ci-cd, failure-analysis, rag, github-actions, llm

---

## Overview

A GitHub Action that triggers on CI failures and uses RAG to explain what went wrong, suggest fixes, and link to relevant past resolutions — reducing mean time to recovery (MTTR).

## Architecture

```
┌────────────────────────────────────────────────────────────┐
│                  CI Pipeline (GitHub Actions)               │
│                                                            │
│  job: test ── FAILED ──▶ on: failure                       │
│                                  │                         │
│                                  ▼                         │
│              ┌─────────────────────────────────┐           │
│              │   Failure Explainer Action      │           │
│              │                                 │           │
│              │  ┌──────────┐  ┌────────────┐   │           │
│              │  │ Log      │  │ Context    │   │           │
│              │  │ Fetcher  │──▶│ Builder    │   │           │
│              │  └──────────┘  └─────┬──────┘   │           │
│              │                       │          │           │
│              │  ┌──────────┐  ┌─────▼──────┐   │           │
│              │  │ RAG      │  │ LLM        │   │           │
│              │  │ Search   │──▶│ Generator  │   │           │
│              │  └──────────┘  └─────┬──────┘   │           │
│              │                       │          │           │
│              │              ┌────────▼──────┐   │           │
│              │              │ Comment on    │   │           │
│              │              │ PR / Issue    │   │           │
│              │              └───────────────┘   │           │
│              └─────────────────────────────────┘           │
└────────────────────────────────────────────────────────────┘
```

## How It Works

### Input Collection
When a job fails:
1. Fetch the failing job's logs (GitHub API)
2. Extract error messages, stack traces, test names
3. Gather context: recent commits, changed files, PR info

### Context Building
Assemble a structured context block:
```markdown
## CI Failure Summary
- Pipeline: build-test-deploy
- Failed job: test-python-3.11
- Error: AssertionError: expected 200, got 500
- Related commit: abc1234 - "fix: update auth middleware"
- Changed files: src/auth/middleware.py, tests/test_auth.py
- Last passing build: 2 hours ago
```

### RAG Retrieval
Search knowledge base for similar failures:
- **Past failure reports** (stored after each incident)
- **Documentation** (readmes, contributing guides)
- **Stack Overflow / GitHub issues** (offline cache)

### LLM Analysis
Generate human-readable explanation:
- What likely caused the failure
- Which change introduced it
- Suggested fix with code snippet
- Link to similar resolved issues

### Output
Post comment on the failing PR:
```
🔍 CI Failure Analysis

The test `test_auth_header` failed with a 500 error.
This was likely caused by the middleware change in commit abc1234.

💡 Suggested Fix:
Check that the middleware properly handles missing headers...

📚 Related: 2 past similar failures resolved here...
```

## Knowledge Base Structure

Stored in repository as markdown files under `.ci-knowledge/`:

```
.ci-knowledge/
├── failures/
│   ├── 2026-08-15-auth-middleware-500.md
│   ├── 2026-08-10-db-connection-timeout.md
│   └── ...
├── runbooks/
│   ├── restart-services.md
│   ├── clear-cache.md
│   └── ...
└── embeddings.db  (ChromaDB)
```

## Tools

- **TypeScript** (GitHub Action)
- **Node.js** runtime for action
- **ChromaDB** (embedded) for RAG
- **OpenAI API** or **Ollama** (local fallback)
- **GitHub API** for log fetching and commenting

## Learning Goals

- GitHub Actions development
- CI/CD failure analysis patterns
- RAG implementation for operational data
- Prompt engineering for code analysis
- Action packaging and publishing

## Build Milestones

1. [ ] Create GitHub Action skeleton with failure event trigger
2. [ ] Implement log fetching and parsing
3. [ ] Build context assembly from PR metadata
4. [ ] Set up ChromaDB with knowledge base
5. [ ] Implement RAG retrieval for similar failures
6. [ ] Design LLM prompt for failure explanation
7. [ ] Add PR comment generation
8. [ ] Support local Ollama fallback (no API key needed)
9. [ ] Publish as reusable GitHub Action

---
*Generated: 2026-08-27*
