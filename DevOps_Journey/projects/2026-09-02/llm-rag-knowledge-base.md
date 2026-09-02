# Project: LLM-Powered Knowledge Base with RAG

## Overview
Build a Retrieval-Augmented Generation (RAG) system that indexes documents and answers questions using embeddings, vector search, and large language models. Includes document ingestion, semantic search, and conversational interface.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│               RAG Knowledge Base System                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Document Pipeline (Ingestion)                              │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│  │ Upload   │  │ Parse    │  │ Chunk    │  │ Embed    │   │
│  │ PDF/TXT  │  │ Extract  │  │ Split    │  │ Generate │   │
│  └──────────┘  └──────────┘  └──────────┘  └────┬─────┘   │
│                                                  │         │
│                                                  ▼         │
│                                          ┌──────────┐     │
│                                          │ Vector   │     │
│                                          │ Database │     │
│                                          │ (Chroma) │     │
│                                          └──────────┘     │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│  Query Pipeline (Retrieval + Generation)                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  User Question                                              │
│       │                                                     │
│       ▼                                                     │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐                 │
│  │ Embed    │  │ Similar  │  │ Retrieve │                 │
│  │ Query    │  │ Search   │  │ Context  │                 │
│  └──────────┘  └──────────┘  └────┬─────┘                 │
│                                   │                        │
│                                   ▼                        │
│                          ┌─────────────────┐               │
│                          │  LLM Prompt     │               │
│                          │  (Question +    │               │
│                          │   Context)      │               │
│                          └────────┬────────┘               │
│                                   │                        │
│                                   ▼                        │
│                          ┌─────────────────┐               │
│                          │  Generated      │               │
│                          │  Answer         │               │
│                          └─────────────────┘               │
└─────────────────────────────────────────────────────────────┘
```

## Features
1. **Multi-format ingestion:** PDF, Markdown, Text, HTML
2. **Smart chunking:** Semantic boundaries, overlap handling
3. **Hybrid search:** Dense embeddings + BM25 keyword matching
4. **Conversation history:** Multi-turn dialogue support
5. **Source attribution:** Citation of retrieved documents

## Tools
- Python
- LangChain / LlamaIndex
- ChromaDB / Weaviate (vector store)
- OpenAI / Ollama (embeddings + LLM)
- FastAPI (backend)
- Streamlit (frontend demo)

## Learning Goals
- Embedding generation and comparison
- Vector database operations
- RAG pipeline optimization
- Prompt engineering for QA
- Evaluation metrics (RAGAS)

## Build Milestones
- [ ] Week 1: Document ingestion pipeline
- [ ] Week 2: Chunking strategies and embeddings
- [ ] Week 3: Vector database setup
- [ ] Week 4: Simple retrieval system
- [ ] Week 5: LLM integration and prompting
- [ ] Week 6: Conversation history support
- [ ] Week 7: Frontend interface (Streamlit)
- [ ] Week 8: Evaluation and optimization
