# Project: AI-Powered Code Review Assistant

## Overview
Create a GitHub App that uses LLMs to automatically review pull requests, suggesting improvements, identifying bugs, and checking code style. Integrates with PR comments and supports custom review rules.

## Architecture
```
GitHub PR → Webhook → Review Engine → LLM API → Comment Generator → PR Comment
                   ↓
              Rule Engine
                   ↓
           Custom Checks
```

## Workflow
1. Trigger on PR opened/updated via GitHub webhook
2. Extract changed files and diff
3. Run rule-based checks (style, security, complexity)
4. Send diff to LLM for semantic review
5. Aggregate findings and suggestions
6. Post structured comment on PR
7. Optionally create follow-up issues for critical problems

## Tools
- **GitHub Actions** + **Python** for webhook handler
- **GitHub CLI** or **PyGithub** for API interactions
- **Claude** or **GPT-4** via API for review generation
- **ruff**, **bandit** for static analysis
- **Flask** or **FastAPI** for webhook server

## Learning Goals
- GitHub App development
- LLM integration for code analysis
- Static code analysis tools
- Automated review workflows

## Build Milestones
- [ ] Week 1: GitHub App setup and webhook handler
- [ ] Week 2: Rule-based checks integration
- [ ] Week 3: LLM review prompt engineering
- [ ] Week 4: Comment generation and posting
- [ ] Week 5: Custom rules and configuration UI

## Estimated Time
3-4 weeks (part-time)

## Difficulty
Intermediate — combines web dev with LLM integration
