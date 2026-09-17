# Local RAG Document Q&A System

## Overview
Build a retrieval-augmented generation (RAG) system that allows users to query documents using natural language, with embeddings stored locally for privacy and offline operation.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                    User Interface                           │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐                    │
│  │  Upload  │ │  Query   │ │  History │                    │
│  │  Docs    │ │  Box     │ │  View    │                    │
│  └──────────┘ └──────────┘ └──────────┘                    │
└─────────────────────────────────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                 Query Processing                            │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │  Text        │  │  Embedding   │  │  Semantic    │      │
│  │  Preprocess  │  │  Generation  │  │  Search      │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                          │
                          ▼ Retrieve
┌─────────────────────────────────────────────────────────────┐
│                  Vector Store                               │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  ChromaDB / LanceDB / FAISS (Local)                  │  │
│  │  - Document embeddings                               │  │
│  │  - Metadata tags                                     │  │
│  │  - Similarity search                                 │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                          │
                          ▼ Augment
┌─────────────────────────────────────────────────────────────┐
│                 Response Generation                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │  Local LLM   │  │  Prompt      │  │  Post-       │      │
│  │  (Ollama)    │  │  Construction│  │  Processing  │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
```

## Workflow
1. User uploads documents (PDF, TXT, Markdown)
2. Documents are chunked and embedded locally
3. Embeddings stored in vector database
4. User submits natural language query
5. Query embedded and searched in vector store
6. Top-k relevant chunks retrieved
7. Chunks combined with query into prompt
8. Local LLM generates answer with citations
9. Response displayed with source references

## Tools
- **Ollama** for local LLM inference
- **LangChain** or **LlamaIndex** for RAG framework
- **ChromaDB** or **LanceDB** for vector storage
- **sentence-transformers** for embedding generation
- **Gradio** or **Streamlit** for UI
- **Python** for backend logic

## Learning Goals
- RAG architecture patterns
- Vector databases and similarity search
- Local LLM deployment and optimization
- Document processing and chunking strategies

## Build Milestones
1. **Week 1**: Set up Ollama and test local LLM
2. **Week 2**: Implement document upload and chunking
3. **Week 3**: Generate embeddings and store in vector DB
4. **Week 4**: Build semantic search and retrieval
5. **Week 5**: Implement RAG pipeline with prompt engineering
6. **Week 6**: Create UI and add conversation history
