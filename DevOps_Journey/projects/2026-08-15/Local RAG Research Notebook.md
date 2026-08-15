# Local RAG Research Notebook

## Overview
A research note-taking application with RAG (Retrieval-Augmented Generation) capabilities that allows querying personal notes using a local LLM.

## Architecture
```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Frontend  │     │   API       │     │  Vector     │
│   (Web)     │◄───▶│  (Python)   │◄───▶│  Database   │
└─────────────┘     └─────────────┘     └─────────────┘
        │                │
   ┌─────────┐     ┌───────────┐
   │  Chat   │     │  Embedding│
   │  UI     │     │  Model    │
   └─────────┘     └───────────┘
```

## Workflow
1. **Import**: Upload documents, notes, PDFs
2. **Embed**: Generate vector embeddings using local model
3. **Store**: Save embeddings in vector database
4. **Query**: Retrieve relevant chunks for questions
5. **Generate**: Create answers using local LLM

## Tools
- Python with FastAPI or Flask
- ChromaDB or Weaviate for vector storage
- Ollama or llama.cpp for local LLM
- LangChain or LlamaIndex for RAG pipeline
- Gradio or Streamlit for UI

## Learning Goals
- Implement RAG systems
- Learn vector databases
- Practice local LLM deployment
- Understand information retrieval

## Build Milestones
1. **M1**: Basic document ingestion and embedding
2. **M2**: Vector database integration
3. **M3**: Implement retrieval pipeline
4. **M4**: Add local LLM for answer generation
5. **M5**: Build conversational UI
6. **M6**: Add multi-document search and citation
