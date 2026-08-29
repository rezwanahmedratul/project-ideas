# AI-Powered Commit Message Generator

## Overview
A git hook and CLI tool that analyzes code diffs and automatically generates well-formatted commit messages following conventional commits standards. Uses a local LLM (via Ollama) to understand context and produce meaningful, descriptive messages without API costs.

## Architecture / Structure
- **Git Hook**: Pre-commit hook that triggers message generation
- **Diff Analyzer**: Extracts changed files, lines added/removed, and file types
- **LLM Interface**: Calls local Ollama model with structured prompt
- **Formatter**: Enforces conventional commits format (feat:, fix:, chore:, etc.)
- **CLI Mode**: Standalone tool for manual message generation

## Workflow
1. Developer stages changes and runs git commit
2. Hook captures the staged diff
3. Sends diff summary + file list to local Ollama instance
4. Receives suggested commit message in conventional format
5. Presents suggestion for review/accept/reject
6. Accepts and applies to commit, or allows manual edit

## Tools
- Python or Go for git hook implementation
- Ollama with Llama 3 or Phi-3 for local inference
- git Python library for hook orchestration
- Conventional Commits spec parser
- ripgrep for diff analysis

## Learning Goals
- Git hooks and pre-commit workflows
- Local LLM integration patterns
- Conventional commits and semantic versioning
- Diff parsing and change summarization

## Build Milestones
1. Week 1: Git hook skeleton that captures staged diffs
2. Week 2: Ollama integration with structured prompts
3. Week 3: Conventional commits format enforcement
4. Week 4: CLI standalone mode with file path input
5. Week 5: Multi-language support and context awareness
6. Week 6: IDE extensions (VS Code, JetBrains) and documentation
