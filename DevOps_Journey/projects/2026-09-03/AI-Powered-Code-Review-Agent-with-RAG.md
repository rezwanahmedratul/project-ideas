# AI Code Review Agent with RAG
**Date:** 2026-09-03  
**Category:** AI/ML  
**Complexity:** Advanced

---

## Overview

Build an AI-powered code review agent that combines LLM analysis with RAG (Retrieval-Augmented Generation) to provide contextual feedback based on project patterns, historical reviews, and coding standards.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│            AI Code Review Agent with RAG                   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  GitHub/GitLab Webhook ─────────────────────────▶          │
│                           │                                 │
│                    ┌──────▼───────────┐                    │
│                    │   PR Parser      │                    │
│                    │   • Diff extract │                    │
│                    │   • Files list   │                    │
│                    │   • Metadata     │                    │
│                    └──────┬───────────┘                    │
│                           │                                │
│                    ┌──────▼───────────┐                    │
│                    │   Context        │                    │
│                    │   Collector      │                    │
│                    │   • Related files│                    │
│                    │   • Git history  │                    │
│                    │   • Doc strings  │                    │
│                    └──────┬───────────┘                    │
│                           │                                │
│                    ┌──────▼───────────┐                    │
│                    │   RAG Retrieval  │                    │
│                    │   • Embeddings   │                    │
│                    │   • Vector DB    │                    │
│                    │   • Relevance    │                    │
│                    └──────┬───────────┘                    │
│                           │                                │
│                    ┌──────▼───────────┐                    │
│                    │   LLM Analyzer   │                    │
│                    │   • Security     │                    │
│                    │   • Performance  │                    │
│                    │   • Style        │                    │
│                    │   • Patterns     │                    │
│                    └──────┬───────────┘                    │
│                           │                                │
│                    ┌──────▼───────────┐                    │
│                    │   Comment        │                    │
│                    │   Generator      │                    │
│                    │   • Inline       │                    │
│                    │   • Summary      │                    │
│                    │   • Suggestions  │                    │
│                    └──────┬───────────┘                    │
│                           │                                │
│                    ┌──────▼───────────┐                    │
│                    │   PR Review      │                    │
│                    │   Post           │                    │
│                    └──────────────────┘                    │
│                                                             │
│  Knowledge Base (Updated after each review)                 │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  • Approved patterns                                  │   │
│  │  • Common anti-patterns                              │   │
│  │  • Team conventions                                  │   │
│  │  • Historical decisions                              │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## Review Categories

### Security Checks
- SQL injection vulnerabilities
- Hardcoded credentials
- Insecure dependencies
- Missing input validation
- CSRF/XSS vulnerabilities

### Performance Issues
- N+1 query patterns
- Inefficient algorithms
- Memory leaks
- Unnecessary allocations
- Missing caching

### Code Quality
- Naming conventions
- Function length
- Duplication
- Complexity metrics
- Error handling

### Style Consistency
- Project-specific patterns
- Team conventions
- Documentation standards
- Test coverage

## RAG Integration

```python
from langchain.vectorstores import Chroma
from langchain.embeddings import HuggingFaceEmbeddings
from langchain.llms import Ollama

vectorstore = Chroma(
    collection_name="code_patterns",
    embedding_function=HuggingFaceEmbeddings()
)

def retrieve_context(code_snippet: str, top_k: int = 5) -> list[str]:
    """Find similar code patterns from knowledge base"""
    results = vectorstore.similarity_search(code_snippet, k=top_k)
    return [doc.page_content for doc in results]

def generate_review(diff: str, context: list[str]) -> dict:
    prompt = f"""
    You are an expert code reviewer. Review the following diff:
    
    === DIFF ===
    {diff}
    
    === CONTEXT (similar patterns from codebase) ===
    {chr(10).join(context)}
    
    Provide:
    1. Security issues (critical, high, medium, low)
    2. Performance concerns
    3. Code quality suggestions
    4. Overall assessment
    
    Be specific with line numbers and actionable advice.
    """
    response = llm(prompt)
    return parse_review(response)
```

## Feedback Format

```markdown
## Code Review: feat/add-user-authentication

**Files Changed:** 5  
**Lines Added:** 142  
**Review Time:** 2.3s

### Critical Issues
- `auth/service.go:45` - SQL injection vulnerability in query construction
  - Use parameterized queries instead of string concatenation
- `config/secret.go:12` - Hardcoded API key detected
  - Move to environment variable or secrets manager

### Warnings
- `handlers/user.go:78` - Missing error handling for database operation
- `middleware/auth.go:34` - Token validation doesn't check expiry

### Suggestions
- Consider extracting validation logic into shared helper
- Add unit tests for edge cases in authentication flow

### Positive Notes
- Good use of context for cancellation
- Clean separation of concerns in handler layer
```

## Tools & Technologies

- **Python** for agent orchestration
- **LangChain** or **LlamaIndex** for RAG
- **Ollama** for local LLM inference
- **ChromaDB** for vector storage
- **GitHub API** for PR integration
- **tree-sitter** for code parsing

## Learning Goals

- Implement RAG pipelines for code analysis
- Understand code review automation
- Build GitHub app integrations
- Master prompt engineering for technical tasks
- Create AI-assisted development workflows

## Build Milestones

| Milestone | Description |
|-----------|-------------|
| M1 | Set up GitHub app with PR webhook |
| M2 | Build diff parser and file extractor |
| M3 | Implement basic LLM code analysis |
| M4 | Add RAG with code pattern database |
| M5 | Create structured feedback generator |
| M6 | Build knowledge base with continuous learning |

## Reference Links

- [GitHub Webhooks Documentation](https://docs.github.com/en/webhooks)
- [LangChain Code Analysis](https://python.langchain.com/docs/use_cases/code)
- [Prompt Engineering Guide](https://www.promptingguide.ai/)
- [Code Review Best Practices](https://www.atlassian.com/git/tutorials/comparing-workflows)
