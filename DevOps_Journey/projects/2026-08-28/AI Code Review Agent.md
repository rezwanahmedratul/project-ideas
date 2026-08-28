# AI/ML: AI Code Review Agent

## Overview
Build an AI agent that integrates into GitHub pull requests and performs thorough code reviews — checking for bugs, security vulnerabilities, performance issues, and style violations — using a combination of rule-based linters and LLM analysis.

## Architecture
```
GitHub Webhook → Review Orchestrator
                         ├── Static Analyzer (ruff, eslint, bandit)
                         ├── Security Scanner (semgrep, trivy)
                         ├── LLM Reviewer (Claude/GPT prompt-based)
                         └── Comment Poster (GitHub PR API)
```

## Workflow
1. PR opened or updated → webhook triggers review
2. Run static analysis linters in parallel
3. Run security scanning tools
4. Feed code diff + findings to LLM for contextual review
5. Post structured comments on PR with severity labels
6. Optionally suggest inline fixes

## Tools
Python, GitHub Actions API, ruff, semgrep, Claude/OpenAI API, FastAPI

## Learning Goals
- GitHub App and webhook development
- Static analysis toolchain integration
- LLM prompt engineering for code review
- Automated vulnerability detection

## Build Milestones
1. Build GitHub App that listens to PR events
2. Integrate ruff/bandit for static analysis
3. Add semgrep for security pattern matching
4. Implement LLM-based contextual review
5. Add inline suggestion feature with diff application
