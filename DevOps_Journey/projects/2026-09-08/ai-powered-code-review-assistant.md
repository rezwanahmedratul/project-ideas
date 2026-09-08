# Project: AI-Powered Code Review Assistant

## Overview
Develop an intelligent code review system that analyzes pull requests, suggests improvements, detects bugs, and explains complex code changes in natural language using LLMs.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────────────┐
│              Code Review Assistant                           │
│  ┌─────────────┐  ┌─────────────┐  �l──────────────────┐   │
│  │ PR          │  │ Analysis    │  │ Explanation     │   │
│  │ Parser      │  │ Engine      │  │ Generator       │   │
│  └─────────────┘  └─────────────┘  └──────────────────┘   │
│                                                           │
│  ┌─────────────────────────────────────────────────────┐  │
│  │              LLM Integration Layer                   │  │
│  │  · Context building · Prompt engineering · Rate limiting│
│  └─────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

## Workflow
1. **Trigger**: Detect new pull request
2. **Context**: Gather files, history, related issues
3. **Analyze**: Run static analysis + AI review
4. **Generate**: Create review comments and suggestions
5. **Post**: Submit review to PR
6. **Learn**: Collect feedback to improve model

## Tools
- GitHub API / GitLab API
- Claude/OpenAI API
- Python (pydantic, httpx)
- Docker for containerization
- PostgreSQL for comment storage

## Learning Goals
- API integration patterns
- Prompt engineering
- Code analysis techniques
- GitHub Apps development

## Build Milestones
1. Week 1: GitHub app skeleton
2. Week 2: PR context builder
3. Week 3: AI analysis pipeline
4. Week 4: Comment generation
5. Week 5: Inline suggestions
6. Week 6: Feedback loop and improvement
