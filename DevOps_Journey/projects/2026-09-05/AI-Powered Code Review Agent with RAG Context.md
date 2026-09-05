# AI-Powered Code Review Agent with RAG Context

## Overview

Build an autonomous code review agent that uses Retrieval-Augmented Generation (RAG) to provide contextual feedback based on your codebase history, style guidelines, and architectural patterns. The agent learns your conventions and improves suggestions over time.

## Architecture

```
┌─────────────────────────────────────────────┐
│        AI Code Review Agent                  │
│                                             │
│  ┌─────────────┐  ┌──────────────────────┐  │
│  │ Code Parser │  │ Vector Database      │  │
│  │ (AST/Tree-sitter)│ (Chroma/PGVector) │  │
│  └─────────────┘  └──────────────────────┘  │
│                        ↓                    │
│  ┌─────────────┐  ┌──────────────────────┐  │
│  │ RAG Engine │  │ LLM Reviewer         │  │
│  │ (Query builder)│ (Contextual prompts)│  │
│  └─────────────┘  └──────────────────────┘  │
│                        ↓                    │
│  ┌─────────────────────────────────────┐   │
│  │ Feedback Generator                 │   │
│  │ - Inline comments                  │   │
│  │ - Severity classification          │   │
│  │ - Auto-fix suggestions             │   │
│  └─────────────────────────────────────┘   │
└─────────────────────────────────────────────┘
```

## Workflow

1. **Indexing**: Parse repository code into semantic chunks stored in vector database
2. **Review Trigger**: Monitor PRs/commits for review requests
3. **Retrieval**: Query similar code patterns and style guidelines from knowledge base
4. **Analysis**: Generate contextual review with references to existing patterns
5. **Learning**: Record reviewer acceptance/rejection to improve future suggestions

## Tools

- Python with LangChain/LlamaIndex for RAG
- ChromaDB or pgvector for embeddings
- Tree-sitter for AST parsing
- Claude/GPT-4 for review generation
- GitHub/GitLab API for integration

## Learning Goals

- Master RAG pipeline construction and optimization
- Understand embedding-based code similarity
- Learn parser-based static analysis integration
- Practice prompt engineering for code review tasks

## Build Milestones

1. **Week 1**: Build code indexer with chunking strategy
2. **Week 2**: Implement vector search and retrieval pipeline
3. **Week 3**: Create review generation with context injection
4. **Week 4**: Add interactive feedback loop for learning
5. **Week 5**: Integrate with GitHub Pull Request workflow
