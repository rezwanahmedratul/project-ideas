# GitHub Issue Triage with LLM Classification

## Overview
Automated issue triage system that classifies GitHub issues by type, priority, and assignment using a fine-tuned or prompted LLM. Reduces maintainer overhead and ensures consistent issue handling across repositories.

## Architecture / Structure
- **Webhook Handler**: Receives GitHub events (issues, comments, labels)
- **Classifier**: LLM-based categorization into bug/enhancement/question/spam
- **Priority Scorer**: Assigns urgency based on content, reporter history, impact signals
- **Labeler**: Auto-applies relevant labels from configured taxonomy
- **Assigner**: Suggests or auto-assigns based on component ownership
- **Analytics Dashboard**: Metrics on triage accuracy and processing volume

## Workflow
1. GitHub webhook triggers on new issue/comment
2. Extract issue title, body, labels, and conversation history
3. Send to LLM with triage prompt template
4. Parse structured response: category, priority, suggested labels
5. Apply labels and assignee via GitHub API
6. Post comment explaining triage decision
7. Log to analytics for continuous improvement

## Tools
- GitHub Actions or webhooks with Python FastAPI
- Ollama for local LLM inference
- PyGithub or GitHub REST API
- SQLite for triage history and analytics
- Docker for containerized deployment

## Learning Goals
- GitHub API and webhook integration
- LLM prompt engineering for classification tasks
- Text classification and sentiment analysis
- Automated workflow design for software projects
- Analytics and metrics collection

## Build Milestones
1. Week 1: GitHub webhook receiver with basic issue parsing
2. Week 2: LLM classification prompt design and testing
3. Week 3: Priority scoring algorithm with edge case handling
4. Week 4: Auto-labeling with configurable taxonomy
5. Week 5: Assignment suggestions using repository map
6. Week 6: Dashboard with triage statistics and accuracy tracking
