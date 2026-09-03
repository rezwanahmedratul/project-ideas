# GitHub Issue Triage with LLM Classification
**Date:** 2026-09-03  
**Category:** AI/ML  
**Complexity:** Intermediate

---

## Overview

Build an AI-powered issue triage system that automatically classifies, prioritizes, and routes GitHub issues using large language models. The system learns from historical triage decisions and improves over time.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│              GitHub Issue Triager                           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  GitHub Webhook ─────────────────────────────────▶          │
│                            │                                │
│                    ┌───────▼───────────┐                   │
│                    │   Preprocessing   │                   │
│                    │   • Title parse   │                   │
│                    │   • Body clean    │                   │
│                    │   • Labels extract│                   │
│                    └───────┬───────────┘                   │
│                            │                               │
│                    ┌───────▼───────────┐                   │
│                    │   LLM Classifier  │                   │
│                    │   • Type: Bug/    │                   │
│                    │     Feature/Docs  │                   │
│                    │   • Priority:     │                   │
│                    │     Critical/High │                   │
│                    │     Medium/Low    │                   │
│                    │   • Component:    │                   │
│                    │     Frontend/     │                   │
│                    │     Backend/API   │                   │
│                    └───────┬───────────┘                   │
│                            │                               │
│                    ┌───────▼───────────┐                   │
│                    │   Confidence      │                   │
│                    │   Scorer          │                   │
│                    │   • Auto-triage   │                   │
│                    │     (>90%)        │                   │
│                    │   • Human review  │                   │
│                    │     (<70%)        │                   │
│                    └───────┬───────────┘                   │
│                            │                               │
│                    ┌───────▼───────────┐                   │
│                    │   Action Router   │                   │
│                    │   • Apply labels  │                   │
│                    │   • Assign owner  │                   │
│                    │   • Set milestone │                   │
│                    └───────────────────┘                   │
│                                                             │
│  Feedback Loop ─────────────────────────────────▶           │
│  (Human corrections improve model)                          │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## Classification Schema

### Issue Types
| Type | Indicators | Priority Weight |
|------|------------|-----------------|
| Bug | error, crash, fail, broken, not working | High |
| Feature | want, need, should have, enhancement | Medium |
| Documentation | docs, readme, guide, tutorial | Low |
| Question | how, why, what is, help | Medium |
| Security | vuln, exploit, leak, credential | Critical |

### Priority Levels
- **Critical**: System down, data loss, security breach
- **High**: Major feature broken, workaround unavailable
- **Medium**: Minor issue, partial functionality lost
- **Low**: Cosmetic, enhancement request, nice-to-have

## Model Approach

### Option 1: Fine-tuned Small Model
- Base model: Llama 3.1 8B or Mistral 7B
- Fine-tune on GitHub issue dataset
- Deploy locally for privacy

### Option 2: Prompt-based with LLM API
- Use GPT-4o or Claude 3.5
- Structured prompt with few-shot examples
- Extract JSON output with pydantic

### Option 3: Hybrid Approach
- Fast classifier (embeddings + softmax) for initial routing
- LLM for complex cases requiring reasoning
- Human-in-the-loop for low-confidence predictions

## Tools & Technologies

- **Python** with `github3.py` or GraphQL API
- **LangChain** or **LlamaIndex** for LLM orchestration
- **FastAPI** for webhook endpoint
- **PostgreSQL** for issue history and feedback
- **Redis** for caching embeddings
- **Weaviate** or **pgvector** for semantic search

## Learning Goals

- Understand LLM prompt engineering techniques
- Learn GitHub API integration patterns
- Implement human-in-the-loop ML systems
- Practice webhook handling and async processing
- Design feedback loops for continuous improvement

## Build Milestones

| Milestone | Description |
|-----------|-------------|
| M1 | Set up GitHub app with webhook subscription |
| M2 | Build issue preprocessing pipeline |
| M3 | Implement basic LLM classification |
| M4 | Add confidence scoring and routing logic |
| M5 | Create feedback collection interface |
| M6 | Build dashboard with triage statistics |

## Reference Links

- [GitHub Webhooks Documentation](https://docs.github.com/en/webhooks)
- [LangChain GitHub Integration](https://python.langchain.com/docs/integrations/providers/github)
- [Prompt Engineering Guide](https://www.promptingguide.ai/)
