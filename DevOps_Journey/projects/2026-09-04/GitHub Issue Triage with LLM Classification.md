# GitHub Issue Triage with LLM Classification

## Overview
A GitHub Action that automatically triages incoming issues using LLM classification, suggesting labels, assignees, and priority based on issue content and project history.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────────┐
│            GitHub Issue Triage System                    │
├─────────────┬──────────────┬──────────────┬─────────────┤
│  Event      │  LLM         │  History     │  Action     │
│  Listener   │  Classifier  │  Analyzer    │  Runner     │
├─────────────┴──────────────┴──────────────┴─────────────┤
│              GitHub API Integration                      │
└─────────────────────────────────────────────────────────┘
```

## Workflow
1. GitHub Action triggered on issue creation/edit
2. Issue content + project history sent to LLM for analysis
3. LLM suggests labels, assignee, priority, and estimation
4. Action applies suggestions as comments or direct changes
5. Human reviewer can approve, modify, or reject suggestions

## Tools
- GitHub Actions (TypeScript)
- OpenAI API or local LLM (Ollama)
- SQLite for issue history
- GitHub REST/GraphQL API
- Label schema configuration

## Learning Goals
- GitHub Actions development
- LLM prompt engineering for classification
- Issue tracking best practices
- Automation with human oversight

## Build Milestones
1. **M1**: Basic issue classification (bug/feature/question)
2. **M2**: Label suggestion with confidence scores
3. **M3**: Assignee recommendation based on history
4. **M4**: Priority estimation using ML on past data
5. **M5**: Dashboard for triage accuracy tracking
6. **M6**: Full automation with human review gate
