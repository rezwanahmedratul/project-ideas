# Local RAG Code Documentation Bot

## Overview
A self-hosted documentation bot that indexes your codebase using retrieval-augmented generation (RAG) with a local LLM. Answers questions about code structure, API usage, and architecture without relying on external APIs.

## Architecture / Structure
- **Indexer**: Scans codebase and creates vector embeddings of code chunks
- **Embedding Model**: Local embedding model (e.g., BGE, GTE) running via Ollama
- **Vector Store**: ChromaDB or Weaviate for efficient similarity search
- **Question Handler**: Routes queries to appropriate RAG pipeline
- **Response Generator**: Combines retrieved context with question for answer
- **Cache Layer**: Redis for frequent queries to reduce latency

## Workflow
1. Index codebase: parse files, chunk by function/class, embed with local model
2. Store embeddings in ChromaDB with source code references
3. Receive natural language query from user/terminal
4. Query ChromaDB for top-k relevant code chunks
5. Construct prompt with retrieved context + LLM instruction
6. Generate explanation using local LLM
7. Return answer with source citations

## Tools
- Ollama for local LLM serving
- ChromaDB for vector storage
- Python with langchain or llama-index
- Tokenizers for text chunking
- FastAPI for REST interface

## Learning Goals
- RAG system architecture and optimization
- Vector embeddings and semantic search
- Code parsing and AST manipulation
- Local LLM fine-tuning and prompting
- Production deployment of retrieval systems

## Build Milestones
1. Week 1: Basic file indexer with tokenization and chunking
2. Week 2: Embedding generation with local model
3. Week 3: ChromaDB integration and vector storage
4. Week 4: Similarity search and retrieval pipeline
5. Week 5: RAG prompt engineering and response generation
6. Week 6: FastAPI interface with streaming responses and caching
