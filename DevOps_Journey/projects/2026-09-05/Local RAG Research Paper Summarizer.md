# Local RAG Research Paper Summarizer

## Overview

Build a Retrieval-Augmented Generation system specifically designed for academic papers. The system ingests PDF research papers, extracts structured information, and enables conversational queries about methodology, findings, and limitations.

## Architecture

```
┌─────────────────────────────────────────────┐
│       RAG Research Paper System              │
│                                             │
│  ┌─────────────┐  ┌──────────────────────┐  │
│  │ PDF Ingest  │  │ Document Chunker     │  │
│  │ (PyPDF/    │  │ (semantic splitting) │  │
│  │  pdfplumber)│  └──────────────────────┘  │
│  └─────────────┘            ↓               │
│                          ┌─────────────┐   │
│                          │ Embedding   │   │
│                          │ (Local)     │   │
│                          └─────────────┘   │
│                               ↓             │
│  ┌─────────────┐  ┌──────────────────────┐  │
│  │ Query API   │  │ Vector Store         │  │
│  │ (FastAPI)   │  │ (ChromaDB)           │  │
│  └─────────────┘  └──────────────────────┘  │
│                          ↓                  │
│  ┌─────────────────────────────────────┐    │
│  │ LLM Response Generator             │    │
│  │ - Citation-aware answers           │    │
│  │ - Source attribution               │    │
│  └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
```

## Workflow

1. **Ingestion Pipeline**: Parse PDFs, extract text, identify sections (abstract, methods, results)
2. **Chunking Strategy**: Split documents semantically while preserving cross-reference integrity
3. **Embedding Generation**: Create vector representations using local embedding models
4. **Storage**: Index in vector database with metadata for filtering by paper attributes
5. **Query Processing**: Retrieve relevant chunks, synthesize answers with citations

## Tools

- Python with LangChain for pipeline orchestration
- pdfplumber for PDF parsing
- Sentence-Transformers for embeddings (all-MiniLM-L6-v2)
- ChromaDB or LanceDB for vector storage
- Ollama for local LLM inference
- Gradio for interactive web interface

## Learning Goals

- Master document ingestion and preprocessing pipelines
- Understand chunking strategies for different document types
- Learn embedding model selection and fine-tuning
- Practice building citation-aware generation systems

## Build Milestones

1. **Week 1**: PDF parsing and section extraction
2. **Week 2**: Implement semantic chunking and embedding pipeline
3. **Week 3**: Build vector store with metadata filtering
4. **Week 4**: Create query interface with citation generation
5. **Week 5**: Develop interactive dashboard for exploration
