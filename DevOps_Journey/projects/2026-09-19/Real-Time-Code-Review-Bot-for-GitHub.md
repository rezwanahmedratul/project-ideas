# Project: Real-Time Code Review Bot for GitHub

## Overview
Create a GitHub App that provides real-time code review comments on pull requests using AI, focusing on security, performance, and code quality with contextual suggestions.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────┐
│         Real-Time Code Review Bot                   │
├─────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐ │
│  │  GitHub     │  │  AI         │  │  Comment    │ │
│  │  Webhook    │  │  Analyzer   │  │  Generator  │ │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘ │
│         │                 │                 │        │
│         └─────────────────┼─────────────────┘        │
│                           ▼                          │
│                 ┌─────────────────┐                 │
│                 │  Review Engine  │                 │
│                 │  • Security     │                 │
│                 │  • Performance  │                 │
│                 │  • Style        │                 │
│                 └─────────────────┘                 │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Listen for pull_request events via GitHub webhook
2. Extract changed files and diff information
3. Send code snippets to AI analyzer with context
4. Generate review comments categorized by:
   - **Critical**: Security vulnerabilities, bugs
   - **Warning**: Performance issues, anti-patterns
   - **Suggestion**: Style improvements, readability
5. Post inline comments on specific lines
6. Leave summary comment on PR
7. Update PR status check with review results

## Tools
- GitHub Apps API
- Python/FastAPI for webhook handler
- Claude/OpenAI API for analysis
- SQLite for comment history
- Docker for deployment
- GitHub Actions for testing

## Learning Goals
- GitHub Apps development
- Webhook handling and security
- AI prompt engineering for code review
- REST API integration patterns
- Code quality analysis techniques

## Build Milestones
1. **Week 1**: Create GitHub App + webhook handler
2. **Week 2**: Build diff parser and context extractor
3. **Week 3**: Implement AI review engine
4. **Week 4**: Add comment generation and posting
5. **Week 5**: Create web dashboard for configuration
6. **Week 6**: Deploy and test with real repositories
