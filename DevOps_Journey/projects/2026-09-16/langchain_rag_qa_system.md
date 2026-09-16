# Project: LangChain RAG Document Q&A System

## Overview
Build a production-ready Retrieval-Augmented Generation system that answers questions from a custom document corpus. Implements document loading, chunking, embedding, vector storage, and LLM response generation.

## Architecture
```
┌─────────────────┐
│  Documents      │
│  (PDF, MD, TXT) │
└────────┬────────┘
         │ Load & Chunk
         ▼
┌─────────────────┐     ┌─────────────────┐
│   Chunking      │────▶│  Embeddings     │
│  (Recursive,    │     │  (text-embedding│
│   by token size)│     │   3-small)      │
└─────────────────┘     └────────┬────────┘
                                 │
                                 ▼
                         ┌─────────────────┐
                         │  Vector DB      │
                         │  (Chroma/Qdrant)│
                         └────────┬────────┘
                                  │ Retrieve
                                  ▼
┌─────────────────┐     ┌─────────────────┐
│  User Query     │────▶│  RAG Pipeline   │
│                 │     │  + LLM (GPT-4o  │
│                 │     │   / local LLM)  │
└─────────────────┘     └────────┬────────┘
                                 │
                                 ▼
                         ┌─────────────────┐
                         │  Answer +       │
                         │  Citations      │
                         └─────────────────┘
```

## Workflow
1. Ingest documents into the vector store
2. When user asks a question, embed the query
3. Retrieve top-k similar document chunks
4. Construct prompt with retrieved context + question
5. Generate answer with source citations
6. Return answer with confidence scores

## Tools & Tech Stack
- **LangChain/LangGraph** — Orchestration framework
- **Chroma** — Embedded vector database
- **Qdrant** — Alternative: cloud-native vector DB
- **OpenAI embeddings** — text-embedding-3-small
- **LLM**: GPT-4o, Claude, or local Ollama models
- **FastAPI** — REST API layer
- **React/Vite** — Web interface
- **Markdown** — Document format

## Learning Goals
- Document loading strategies (PDF, Markdown, HTML)
- Chunking algorithms and overlap tuning
- Embedding model selection and comparison
- Vector similarity search optimization
- Prompt engineering for RAG
- Evaluation metrics: faithfulness, answer relevance

## Build Milestones
1. [ ] Set up basic LangChain RAG chain
2. [ ] Implement document loader with chunking
3. [ ] Add vector store persistence
4. [ ] Build FastAPI endpoint for queries
5. [ ] Create React chat interface
6. [ ] Add citation tracking and source linking
7. [ ] Implement evaluation pipeline with ragas

## Reference Links
- [LangChain Documentation](https://python.langchain.com/docs/)
- [Ragas — RAG Evaluation Framework](https://docs.ragas.io/)
- [Chroma Documentation](https://docs.trychroma.com/)
- [LlamaIndex (alternative)](https://docs.llamaindex.ai/)
