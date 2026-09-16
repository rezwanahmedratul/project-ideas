# Project: AI-Powered Code Review Bot

## Overview
Build a GitHub App that automatically reviews pull requests using AI. Analyzes code changes, suggests improvements, checks for security issues, and enforces coding standards — all powered by LLM APIs.

## Architecture
```
┌────────────────────────────────────────────────────────────┐
│                       GitHub                                │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐             │
│  │  PR      │    │  Branch  │    │  Commit  │             │
│  │  Created │    │  Pushed  │    │  Pushed  │             │
│  └────┬─────┘    └────┬─────┘    └────┬─────┘             │
│       │               │               │                   │
│       └───────────────┼───────────────┘                   │
│                       │ GitHub Webhook                     │
│                       ▼                                    │
│              ┌─────────────────┐                          │
│              │   Bot Service   │                          │
│              │  (FastAPI)      │                          │
│              └────────┬────────┘                          │
│                       │                                    │
│         ┌─────────────┼─────────────┐                    │
│         ▼             ▼             ▼                     │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐                │
│  │ Code      │  │ Security │  │ Style    │                │
│  │ Analyzer  │  │ Scanner  │  │ Checker  │                │
│  │           │  │          │  │          │                │
│  │• Diff     │  │• Secret  │  │• Linting │                │
│  │• Context  │  │  detection│ │• Format  │                │
│  │• LLM      │  │• Vuln    │  │• Convetion│               │
│  │  review   │  │  scan    │  │• Comments │               │
│  └──────────┘  └──────────┘  └──────────┘                │
│                       │                                    │
│                       ▼                                    │
│              ┌─────────────────┐                          │
│              │  Comment on PR  │                          │
│              │  with findings  │                          │
│              └─────────────────┘                          │
└────────────────────────────────────────────────────────────┘
```

## Workflow
1. Developer opens PR or pushes to branch
2. GitHub webhook triggers bot service
3. Bot fetches PR diff and context (branch, files changed)
4. Parallel analysis: code review, security scan, style check
5. Aggregated results posted as PR comments
6. Optional: add labels, request reviewers based on file types

## Tools & Tech Stack
- **GitHub Apps API** — Webhooks and PR manipulation
- **FastAPI** — Bot service backend
- **Claude/GPT-4** — AI analysis engine
- **Bandit** — Python security scanner
- **Semgrep** — Static analysis for vulnerabilities
- **ruff** — Python linter/formatter
- **Pre-commit hooks** — Pre-merge validation
- **Redis** — Rate limiting and caching

## Learning Goals
- GitHub App development and OAuth flow
- Webhook handling and signature verification
- Diff parsing and context extraction
- Cost optimization for LLM calls (chunking, caching)
- Structured prompt engineering for code review
- Security scanning integration

## Build Milestones
1. [ ] Create GitHub App with webhooks
2. [ ] Build FastAPI service for event handling
3. [ ] Implement diff parsing and context gathering
4. [ ] Integrate Claude/GPT for code review prompts
5. [ ] Add security scanning (Semgrep + Bandit)
6. [ ] Design comment formatting for PR feedback
7. [ ] Deploy with rate limiting and cost controls

## Reference Links
- [GitHub Apps Documentation](https://docs.github.com/en/developers/apps)
- [GitHub Webhooks Guide](https://docs.github.com/en/webhooks/about-webhooks)
- [Semgrep](https://semgrep.dev/)
- [Pre-commit Framework](https://pre-commit.com/)
