# Local LLM-Powered Shell Command Generator

**Category:** AI ML  
**Date:** 2026-08-18  
**Difficulty:** Beginner-Intermediate

---

## Overview

A CLI tool that converts natural language into shell commands using a local LLM (via Ollama). Type `ask "find all large files modified last week"` → get a safe, explained bash command. Runs fully offline on your NixOS machine — no API keys, no cloud.

## Architecture / Structure

```
shell-ai/
├── cmd/
│   └── main.go           # CLI loop
├── internal/
│   ├── llm/              # Ollama client (generate API)
│   ├── prompt/           # System prompt templates
│   ├── safety/           # Danger-pattern checker
│   └── explain/          # Command breakdown renderer
├── templates/
│   └── system.txt        # "You are a unix expert..."
└── config.yaml           # Model name, temp, allowed cmds
```

## Workflow

1. User types natural language request
2. **Prompt** builder injects request + OS info (uname, shell)
3. **LLM** (Ollama, e.g., qwen2.5-coder:7b) returns command + explanation
4. **Safety** layer flags destructive patterns (`rm -rf`, `:(){`)
5. User approves → command executed, output captured
6. **Explain** mode shows what each flag does

## Tools

- **Language:** Go (or Python)
- **LLM Runtime:** Ollama, llama.cpp
- **Models:** qwen2.5-coder:7b, codellama:13b, deepseek-coder
- **Safety:** Regex-based danger detection
- **UI:** Bubble Tea TUI (optional)

## Learning Goals

- Prompt engineering for code generation
- Ollama REST API integration
- Local inference trade-offs (model size vs. accuracy)
- Building safe AI tools (guardrails)

## Build Milestones

| Milestone | Deliverable | Est. Time |
|-----------|-------------|-----------|
| M1 | Ollama client + basic prompt | 0.5 day |
| M2 | Parse + execute returned command | 0.5 day |
| M3 | Safety checker (danger patterns) | 0.5 day |
| M4 | Explanation renderer | 0.5 day |
| M5 | TUI with history (Bubble Tea) | 1 day |

---

**Tags:** #llm #local-ai #ollama #cli #shell #nixos
