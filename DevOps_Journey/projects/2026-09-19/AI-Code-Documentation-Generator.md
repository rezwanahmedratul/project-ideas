# Project: AI Code Documentation Generator

## Overview
Build an AI-powered tool that automatically generates comprehensive documentation for codebases — including READMEs, API docs, architecture diagrams, and inline comments — using LLMs and static analysis.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────┐
│        AI Code Documentation Generator              │
├─────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐ │
│  │  Code       │  │  Analysis   │  │  AI         │ │
│  │  Parser     │  │  Engine     │  │  Generator  │ │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘ │
│         │                 │                 │        │
│         └─────────────────┼─────────────────┘        │
│                           ▼                          │
│                 ┌─────────────────┐                 │
│                 │  Documentation  │                 │
│                 │  Outputs        │                 │
│                 │  • README       │                 │
│                 │  • API Docs     │                 │
│                 │  • Architecture │                 │
│                 └─────────────────┘                 │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Scan repository for source files
2. Parse code structure (classes, functions, imports)
3. Extract existing comments and docstrings
4. Send context to LLM with prompts for:
   - High-level README generation
   - Function/method documentation
   - Architecture overview
   - Usage examples
5. Validate generated content for accuracy
6. Output structured documentation in target formats
7. Integrate with CI/CD for auto-updates

## Tools
- Python with tree-sitter for code parsing
- Anthropic Claude or OpenAI API
- MkDocs or Sphinx for documentation sites
- Mermaid.js for architecture diagrams
- GitHub Actions for automation

## Learning Goals
- Static code analysis techniques
- LLM prompt engineering for code
- Documentation generation patterns
- Multi-format output handling
- CI/CD integration for docs

## Build Milestones
1. **Week 1**: Code parser + structure extraction
2. **Week 2**: Implement README generator
3. **Week 3**: Build API documentation module
4. **Week 4**: Create architecture diagram generator
5. **Week 5**: Add validation and review system
6. **Week 6**: Integrate with CI/CD pipelines
