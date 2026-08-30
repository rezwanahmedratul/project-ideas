# CI Pipeline Failure Explainer with RAG

## Overview
When CI/CD pipelines fail, this tool analyzes build logs, error traces, and recent commits to explain failures in plain language. Uses RAG to match current failures with historical resolved issues for faster troubleshooting.

## Architecture / Structure
- **Log Parser**: Extracts errors, warnings, and stack traces from CI output
- **Context Gatherer**: Fetches recent commits, changed files, and affected tests
- **Embedding Engine**: Converts error patterns to searchable vectors
- **RAG Retriever**: Finds similar historical failures and their resolutions
- **LLM Analyst**: Synthesizes error context + historical patterns into explanation
- **Suggestion Engine**: Recommends fixes with code snippets where applicable

## Workflow
1. CI pipeline fails (GitHub Actions, GitLab CI, Jenkins, etc.)
2. Webhook notifies failure analyzer with build ID and log URL
3. Log parser extracts relevant error messages and stack traces
4. Context gatherer pulls recent commits touching failing areas
5. Embedding engine converts current error to vector representation
6. RAG retriever finds top-k similar past failures with solutions
7. LLM generates natural language explanation: "Test failing because..."
8. Suggestions include specific code changes and related issues
9. Comment posted to PR with diagnosis and fix suggestions

## Tools
- CI platform APIs (GitHub, GitLab, Jenkins)
- Ollama for local LLM inference
- ChromaDB for vector similarity search
- GitPython for commit history analysis
- FastAPI for webhook handling
- Markdown formatting for PR comments

## Learning Goals
- CI/CD pipeline architecture and failure modes
- Log parsing and error pattern recognition
- RAG system design for practical applications
- Cross-platform CI integration patterns
- Developer experience optimization

## Build Milestones
1. Week 1: CI webhook handler and log extraction
2. Week 2: Error pattern parsing and normalization
3. Week 3: Historical failure indexing with embeddings
4. Week 4: RAG retrieval and relevance ranking
5. Week 5: LLM explanation generation and formatting
6. Week 6: PR comment integration and feedback loop
