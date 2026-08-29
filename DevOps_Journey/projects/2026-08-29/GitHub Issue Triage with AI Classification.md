# GitHub Issue Triage with AI Classification

## Overview
A GitHub Action that automatically classifies, prioritizes, and assigns issues using AI analysis of titles, descriptions, and labels. Reduces triage time from hours to seconds and ensures no issue falls through the cracks.

## Architecture / Structure
- **GitHub Action**: Triggers on new issue/pr creation
- **Classifier**: AI model categorizes issue type (bug, feature, docs, test, devops)
- **Priority Assigner**: Estimates urgency based on keywords and project context
- **Label Proposer**: Suggests relevant labels for maintainers to approve
- **Routing Logic**: Auto-assigns to appropriate milestone or team member

## Workflow
1. New issue opened or PR created
2. Action fetches issue body, comments, and project context
3. Sends to Ollama/local LLM with classification prompt
4. LLM returns category, priority score, suggested labels
5. Action applies labels and sets priority milestone
6. Notifies assignee via comment or direct message

## Tools
- GitHub Actions + JavaScript/TypeScript
- Ollama with Llama 3 for local inference
- github-sdk for API interactions
- Express.js or FastAPI for classification service
- SQLite for issue history and learning

## Learning Goals
- GitHub Actions development and workflow automation
- Text classification and intent detection
- Issue tracking and project management workflows
- CI/CD for repository governance

## Build Milestones
1. Week 1: GitHub Action skeleton with issue event listener
2. Week 2: LLM integration for issue classification
3. Week 3: Label suggestion and auto-apply logic
4. Week 4: Priority scoring based on keywords and history
5. Week 5: Milestone assignment and notification system
6. Week 6: Learning from maintainer corrections (feedback loop)
