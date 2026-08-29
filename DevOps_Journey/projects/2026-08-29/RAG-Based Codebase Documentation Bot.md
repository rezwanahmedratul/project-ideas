# RAG-Based Codebase Documentation Bot

## Overview
An AI-powered bot that ingests your codebase and answers architecture questions using retrieval-augmented generation. Developers can ask "how does the auth flow work?" or "what handles payment processing?" and get accurate, sourced answers with code snippets.

## Architecture / Structure
- **Indexer**: Crawls codebase, extracts functions/classes/modules, builds vector embeddings
- **RAG Engine**: Retrieves relevant code snippets using semantic search
- **LLM Interface**: Generates natural language explanations grounded in retrieved code
- **Bot Interface**: Discord/Slack bot or web chat for developer interactions
- **Update Scheduler**: Incremental re-indexing on code changes

## Workflow
1. Indexer scans repo structure and code files
2. Extracts docstrings, function signatures, and key comments
3. Embeds extracted text into vector store (Chroma/Pinecone)
4. User asks question via bot interface
5. System retrieves top-k relevant code snippets
6. LLM generates answer citing specific files and line numbers
7. Developer clicks citations to jump to source

## Tools
- Python + LangChain or LlamaIndex for RAG
- ChromaDB or Weaviate for vector storage
- Ollama/Llama 3 for local inference
- Discord.py or Slack Bolt for bot interface
- Tree-sitter for AST parsing

## Learning Goals
- Retrieval-augmented generation architectures
- Code embedding and semantic search techniques
- Vector database selection and optimization
- Developer tool integration patterns

## Build Milestones
1. Week 1: Codebase crawler and AST extraction
2. Week 2: Vector embedding pipeline with ChromaDB
3. Week 3: RAG query engine with LangChain
4. Week 4: Discord bot integration with slash commands
5. Week 5: Citation linking back to source code
6. Week 6: Incremental indexing and performance optimization
