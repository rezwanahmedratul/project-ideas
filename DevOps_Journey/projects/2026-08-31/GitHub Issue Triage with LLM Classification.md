# GitHub Issue Triage with LLM Classification

**Category:** AI/ML  
**Date:** 2026-08-31

## Overview
An AI-powered GitHub issue triage system that automatically classifies, prioritizes, and suggests assignments for incoming issues using local or API-based LLMs.

## Architecture
```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  GitHub Webhook │────▶│  Issue Parser   │────▶│  Classification│
│  (new issue)    │     │  & Enrichment   │     │  Model         │
└─────────────────┘     └─────────────────┘     └────────┬────────┘
                                                        │
                                              ┌────────▼────────┐
                                              │  Priority      │
                                              │  Scorer        │
                                              └────────┬────────┘
                                                       │
                                              ┌────────▼────────┐
                                              │  Label &       │
                                              │  Assign        │
                                              └─────────────────┘
```

## Workflow
1. GitHub webhook triggers on new issue
2. Parse issue title, body, labels, assignees
3. Classify: bug, feature, docs, question, etc.
4. Estimate priority based on severity indicators
5. Suggest assignees based on past activity
6. Auto-label and optionally auto-assign
7. Log decisions for human review

## Tools
- GitHub REST/GraphQL API
- Python (github-api, fastapi)
- Ollama or API-based LLM
- SQLite for decision history

## Learning Goals
- GitHub API integration
- Text classification with LLMs
- Workflow automation
- Decision logging and auditing

## Build Milestones
- [ ] Week 1: GitHub webhook receiver
- [ ] Week 2: Issue parsing and preprocessing
- [ ] Week 3: Classification model integration
- [ ] Week 4: Priority scoring logic
- [ ] Week 5: Auto-label and assign
- [ ] Week 6: Dashboard and decision review
