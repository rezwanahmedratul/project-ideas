# CI Pipeline Failure Explainer with RAG

## Overview
An AI assistant that analyzes failed CI/CD pipelines, retrieves similar past failures from knowledge base, and suggests targeted fixes with explanations.

## Architecture
```
┌─────────────────────────────────────────────────┐
│         CI/CD Platform (GitHub Actions)         │
│              Failure Event                      │
└──────────────────────┬──────────────────────────┘
                       │
          ┌────────────▼────────────┐
          │  Failure Parser         │
          │  (log extraction)       │
          └────────────┬────────────┘
                       │
          ┌────────────▼────────────┐
          │  Embedding Generator    │
          │  (text → vector)        │
          └────────────┬────────────┘
                       │
          ┌────────────▼────────────┐
          │  Vector Database        │
          │  (failure embeddings)   │
          └────────────┬────────────┘
                       │
          ┌────────────▼────────────┐
          │  RAG Retrieval          │
          │  (similar failures)     │
          └────────────┬────────────┘
                       │
          ┌────────────▼────────────┐
          │  LLM Explanation        │
          │  (root cause + fix)     │
          └────────────┬────────────┘
                       │
          ┌────────────▼────────────┐
          │  GitHub Comment         │
          │  (inline PR feedback)   │
          └─────────────────────────┘
```

## Workflow
1. CI pipeline fails → webhook triggers analysis
2. Extract error logs and context
3. Embed failure description
4. Retrieve top-K similar past failures from vector DB
5. LLM synthesizes root cause and recommended fix
6. Post explanation as GitHub PR comment

## Tools
- **GitHub Actions** for CI
- **ChromaDB** or **Weaviate** for vector storage
- **OpenAI embeddings** or **local embedding model**
- **Python** for orchestration
- **GitHub API** for commenting

## Learning Goals
- Retrieval-Augmented Generation (RAG) patterns
- CI/CD webhook integration
- Error log parsing and normalization
- Knowledge base maintenance

## Build Milestones
1. [ ] CI failure webhook receiver
2. [ ] Log extraction and normalization
3. [ ] Embedding generation pipeline
4. [ ] Vector database for historical failures
5. [ ] Similarity search implementation
6. [ ] LLM explanation generation
7. [ ] GitHub PR comment integration
