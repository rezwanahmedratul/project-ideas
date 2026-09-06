# Local RAG Research Paper Summarizer

## Overview
Create a local RAG system that ingests arXiv papers, generates embeddings, and provides intelligent summarization and Q&A over research literature using open-source models.

## Architecture
```
┌─────────────────────────────────────────┐
│     Research Paper Summarizer           │
├─────────────────────────────────────────┤
│  Ingestion Pipeline                     │
│  ├─ arXiv API integration               │
│  ├─ PDF parsing (marker-pdf)            │
│  └─ Chunking strategy                   │
├─────────────────────────────────────────┤
│  Embedding Store                        │
│  ├─ ChromaDB or Qdrant                  │
│  ├─ Sentence-transformers               │
│  └─ Metadata indexing                   │
├─────────────────────────────────────────┤
│  Query Interface                        │
│  ├─ Natural language questions          │
│  ├─ Semantic search                     │
│  └─ Citation-aware responses            │
└─────────────────────────────────────────┘
```

## Workflow
1. User queries about a research topic
2. System retrieves relevant paper sections
3. LLM synthesizes answer with citations
4. Response includes source references

## Tools
- Ollama with llama3 or mistral
- LangChain or LlamaIndex
- ChromaDB for vector storage
- marker-pdf for document parsing

## Learning Goals
- RAG system architecture
- Vector database operations
- Embedding model selection
- Local LLM deployment

## Build Milestones
- [ ] Week 1: Paper ingestion pipeline
- [ ] Week 2: Embedding generation
- [ ] Week 3: Vector database setup
- [ ] Week 4: Retrieval implementation
- [ ] Week 5: LLM integration
- [ ] Week 6: UI and evaluation
