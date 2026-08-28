# AI/ML: Local-First AI Note Assistant

## Overview
Build a local-first AI note assistant that runs entirely on-device using small open models (via Ollama). It indexes your notes, answers questions about your knowledge base, and suggests connections — all without sending data to external APIs.

## Architecture
```
Notes Directory → Embedding Generator (local model)
                                     ├── Vector Store (ChromaDB)
                                     ├── QA Engine (RAG pipeline)
                                     └── Connection Finder (similarity search)
         ↓
    Desktop App (Tauri/Electron)
```

## Workflow
1. Scan markdown notes directory and generate embeddings locally
2. Store embeddings in ChromaDB with metadata
3. When user asks a question, retrieve top-k relevant chunks
4. Formulate answer using local LLM with retrieved context
5. Also surface semantically related notes automatically

## Tools
Ollama (Phi-3, Llama 3.2), Python, ChromaDB, sentence-transformers, Tauri (desktop), SQLite

## Learning Goals
- Retrieval-Augmented Generation (RAG) pipelines
- Local LLM deployment and fine-tuning
- Vector database operations
- Privacy-first AI application design

## Build Milestones
1. Set up Ollama with a small local model
2. Build note ingestion pipeline with embeddings
3. Implement basic RAG问答
4. Add semantic note recommendations
5. Package as desktop app with Tauri
