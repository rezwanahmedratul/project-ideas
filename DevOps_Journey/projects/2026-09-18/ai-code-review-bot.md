# AI-Powered Code Review Bot

## Overview
Build a GitHub Actions workflow that uses local LLM inference to review pull requests, checking for security vulnerabilities, code style violations, and suggesting improvements with inline comments.

## Architecture
- **GitHub Actions** workflow trigger
- **Local LLM** via Ollama or vLLM
- **Code diff parsing** for PR analysis
- **Comment posting** via GitHub API
- **Security scanning** integration (Semgrep, Bandit)
- **Configuration** for custom rules

## Workflow
1. PR opened or updated → trigger workflow
2. Extract diff and changed files
3. Run static analysis tools (linters, security scanners)
4. Send relevant code sections to LLM for review
5. Parse LLM feedback into structured comments
6. Post comments to PR with line references
7. Generate summary comment with overall assessment

## Tools
- GitHub Actions / Actions SDK
- Ollama or local LLM server
- Semgrep/Bandit for security scanning
- ESLint/Pylint for style checking
- GitHub REST API for comments
- YAML/TOML for configuration

## Learning Goals
- GitHub Actions workflow design
- Local LLM integration patterns
- Static analysis tooling
- Code review automation
- API integration and authentication

## Build Milestones
1. Create basic GitHub Actions workflow
2. Implement diff extraction and parsing
3. Integrate Ollama for code analysis
4. Add security scanning with Semgrep
5. Format LLM output into PR comments
6. Support configurable review rules
7. Add summary report and suggestions

---
*Generated: 2026-09-18 | Source: AI overnight research engine*
