# Local LLM-Powered Code Review Assistant

## Overview
An offline code review tool that runs a local LLM to analyze pull requests, suggest improvements, and catch common bugs — no API calls, full privacy.

## Architecture
```
┌─────────────────────────────────────────────┐
│            Developer Environment             │
│  ┌─────────────┐    ┌─────────────────────┐ │
│  │ IDE / Git   │───▶│  Review Agent       │ │
│  │ Pre-commit  │    │  (Local LLM)        │ │
│  └─────────────┘    └──────────┬──────────┘ │
│                                │             │
│                        ┌───────▼───────┐     │
│                        │  Context      │     │
│                        │  Builder      │     │
│                        │  (diff + repo)│     │
│                        └───────┬───────┘     │
│                                │             │
│                        ┌───────▼───────┐     │
│                        │  Results      │     │
│                        │  (inline      │     │
│                        │  comments)    │     │
│                        └───────────────┘     │
└─────────────────────────────────────────────┘
```

## Workflow
1. Developer opens PR or runs `review-assistant path/to/repo`
2. Tool extracts diff and relevant context (related files, tests)
3. Local LLM analyzes code for issues, suggestions, style
4. Results posted as inline comments or summary report
5. Optionally integrated as pre-commit hook

## Models
- **CodeLlama** (7B/13B/34B) — fine-tuned for code
- **StarCoder2** (7B/15B) — multilingual coding
- **Phind-CodeLlama** — engineering-focused
- **DeepSeek-Coder** — strong benchmark performance

## Tools
- **Ollama** or **llama.cpp** for inference
- **Python** for orchestration
- **GitPython** for diff extraction
- **LangChain** or custom prompt assembly

## Learning Goals
- Local LLM deployment and optimization
- Prompt engineering for code analysis
- Git integration patterns
- Quality assurance in AI-generated reviews

## Build Milestones
1. [ ] Local LLM inference pipeline
2. [ ] Diff parsing and context building
3. [ ] Basic comment generation
4. [ ] Inline PR comments via API
5. [ ] Pre-commit hook integration
6. [ ] Rule-based filtering (reduce noise)
7. [ ] Custom rule definitions (user-configurable)
