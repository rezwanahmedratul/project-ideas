# Project: Multi-Agent AI Meeting Assistant

## Overview
Build a multi-agent system that attends virtual meetings (Zoom/Teams), takes notes, extracts action items, and generates meeting summaries automatically. Uses ReAct pattern for agent coordination.

## Architecture
```
┌────────────────────────────────────────────────────────────┐
│                    Orchestrator Agent                       │
│  (Coordinates workflow, manages state)                      │
└──────────┬────────────────────────────────────┬────────────┘
           │                                    │
    ┌──────┴──────┐                        ┌────┴──────┐
    ▼             ▼                        ▼           ▼
┌─────────┐  ┌──────────┐            ┌──────────┐ ┌──────────┐
│ Audio   │  │ Note     │            │ Action   │ │ Summary  │
│ Handler │  │ Taker    │            │ Tracker  │ │ Generator│
│         │  │          │            │          │ │          │
│• Transcribe│• Structured│• Extract │• Assign   │• Draft    │
│• Speaker  │• Organize  │  items   │  owners  │  summary  │
│  ID      │• Tag topics│• Due     │• Flag     │• Highlight│
│          │            │  dates    │  urgent  │  decisions │
└────┬────┘  └─────┬────┘            └────┬─────┘ └────┬─────┘
     │             │                       │            │
     └─────────────┴───────────────────────┴────────────┘
                            │
                     ┌─────────────┐
                     │  LLM       │
                     │ (Claude/GPT)│
                     └─────────────┘
```

## Workflow
1. Join scheduled meeting via API/webhook
2. Stream audio transcription in real-time
3. Separate agents handle: note-taking, action item extraction, topic tagging
4. Orchestrator synthesizes outputs after meeting ends
5. Generate structured summary and distribute via Slack/email

## Tools & Tech Stack
- **LangGraph** — Multi-agent orchestration
- **OpenAI Whisper** — Speech-to-text
- **Anthropic Claude** — Main reasoning model
- **Zoom/Teams SDK** — Meeting integration
- **PostgreSQL** — Meeting history storage
- **Redis** — Real-time state caching
- **FastAPI** — Webhook endpoints
- **Celery** — Background task processing

## Learning Goals
- Multi-agent architecture patterns
- ReAct loop implementation
- Real-time audio processing
- State management across agents
- Task queue patterns with Celery
- Webhook handling for external services

## Build Milestones
1. [ ] Build transcription pipeline with Whisper
2. [ ] Implement note-taking agent
3. [ ] Create action item extractor
4. [ ] Design orchestrator with LangGraph
5. [ ] Integrate Zoom webhook listener
6. [ ] Add summary generation and delivery
7. [ ] Build web UI for meeting history

## Reference Links
- [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- [Whisper GitHub](https://github.com/openai/whisper)
- [Multi-Agent Systems Paper](https://arxiv.org/abs/2507.11988)
