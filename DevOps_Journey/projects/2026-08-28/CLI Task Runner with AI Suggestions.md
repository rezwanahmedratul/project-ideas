# Software Dev: CLI Task Runner with AI Suggestions

## Overview
Create a terminal-based task runner that learns from a developer's command history and project structure to suggest relevant tasks, commands, and workflows — similar to a smart autocomplete for your entire workflow.

## Architecture
```
Terminal CLI (Rust/Go) → Task Parser
                              ├── History Indexer (sqlite + embeddings)
                              ├── Suggestion Engine (LLM API or local model)
                              └── Context Extractor (git status, file tree, env vars)
```

## Workflow
1. User types partial command or opens the CLI
2. System reads git status, open files, recent commands, project config
3. Generates ranked suggestions based on context + historical patterns
4. User selects suggestion or gets autocompleted command
5. Optionally executes with confirmation

## Tools
Rust or Go, SQLite, ChromaDB (embeddings), OpenAI/Claude API or ollama, fzf

## Learning Goals
- CLI application design and ergonomics
- Vector search for command suggestion
- Context-aware automation
- Shell integration (fish/zsh hooks)

## Build Milestones
1. Build basic CLI with argument parsing and command execution
2. Index recent shell history with embeddings
3. Add context extraction (git, files, env)
4. Integrate LLM for contextual suggestions
5. Add shell hook integration for automatic suggestions on prompt
