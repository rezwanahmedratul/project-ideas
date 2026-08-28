# Software Dev: Personal Knowledge Graph Viewer

## Overview
Build a desktop/web app that ingests markdown notes, creates a knowledge graph visualization, and allows bidirectional linking navigation — inspired by Obsidian's graph view but with AI-powered relationship discovery and semantic search.

## Architecture
```
Note Input (Markdown) → Parser
                              ├── Entity Extractor (NER + LLM)
                              ├── Graph Builder (SQLite + NetworkX)
                              └── Query Engine (semantic search + full-text)
         ↓
    Frontend (Vue/React) ← GraphQL API
         (D3.js force-directed graph)
```

## Workflow
1. Import markdown files from a directory
2. Parse headings, links, and content to build entity graph
3. Use LLM to extract implicit relationships between notes
4. Visualize as interactive force-directed graph
5. Click nodes to navigate; search using semantic embeddings

## Tools
Python, PostgreSQL + pgvector, FastAPI, Vue.js, D3.js, sentence-transformers, Ollama

## Learning Goals
- Graph data modeling and visualization
- Semantic search with embeddings
- Markdown parsing and link extraction
- Full-stack application architecture

## Build Milestones
1. Build markdown parser with wikilink extraction
2. Create graph database schema and populate it
3. Implement D3.js visualization with node interaction
4. Add semantic search using sentence transformers
5. Build AI-powered relationship suggestion engine
