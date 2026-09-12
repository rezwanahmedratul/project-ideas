# Local RAG Document Assistant

## Overview
Create a privacy-focused document Q&A system that runs entirely locally using small language models and vector embeddings for semantic search.

## Architecture
- Embedding model: local embedding model via ONNX
- Vector store: ChromaDB for lightweight persistence
- LLM: Phi-3 or similar small model via llama.cpp
- UI: Streamlit or Gradio web interface
- Processing: LangChain for pipeline orchestration

## Workflow
1. Upload documents (PDF, TXT, Markdown)
2. Chunk and embed documents locally
3. Store vectors in ChromaDB
4. User asks question via chat interface
5. Retrieve relevant chunks and generate answer

## Tools
- Python, LangChain, ChromaDB, llama.cpp, Streamlit

## Learning Goals
- RAG (Retrieval-Augmented Generation) patterns
- Vector database fundamentals
- Local LLM deployment
- Document processing pipelines

## Build Milestones
1. Document ingestion and chunking
2. Embedding generation and storage
3. Semantic search implementation
4. LLM integration for answering
5. Web interface and refinement
