# Local RAG Code Documentation Bot

## Overview
A local RAG (Retrieval-Augmented Generation) system that indexes a codebase and answers developer questions about the code using a local LLM, with full privacy and offline capability.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────────┐
│            Local RAG Documentation Bot                   │
├─────────────┬──────────────┬──────────────┬─────────────┤
│  Code       │  Embedding   │  LLM         │  Chat       │
│  Indexer    │    Model     │    Engine    │  Interface  │
├─────────────┴──────────────┴──────────────┴─────────────┤
│              Local Vector Store (Chroma/FAISS)           │
└─────────────────────────────────────────────────────────┘
```

## Workflow
1. Indexer parses codebase into semantic chunks (functions, classes, modules)
2. Embedding model converts chunks to vectors stored in local vector DB
3. User asks question via CLI or web interface
4. System retrieves relevant code chunks using similarity search
5. LLM generates answer grounded in retrieved code context

## Tools
- Ollama (llama3.2, qwen2.5) for local LLM
- ChromaDB for vector storage
- LangChain or LlamaIndex for RAG orchestration
- AST parsing for code chunking
- FastAPI for chat interface

## Learning Goals
- RAG system architecture
- Code parsing and semantic chunking
- Local LLM deployment and optimization
- Vector database operations

## Build Milestones
1. **M1**: Basic code indexing with AST parser
2. **M2**: Embedding generation and vector storage
3. **M3**: Similarity search and retrieval
4. **M4**: LLM-powered question answering
5. **M5**: CLI chat interface
6. **M6**: Web interface with conversation history
