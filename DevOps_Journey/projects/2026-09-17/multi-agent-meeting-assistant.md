# Multi-Agent Meeting Assistant

## Overview
Build a multi-agent system that automates meeting workflows: transcription, note-taking, action item extraction, and follow-up scheduling.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                    Meeting Input                            │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Audio Recording (Zoom/Meet/Recorder)                │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                          │
                          ▼ Transcribe
┌─────────────────────────────────────────────────────────────┐
│                 Agent Team                                   │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │Transcription │  │ Summary      │  │ Action Item  │      │
│  │Agent         │  │Agent         │  │Extractor      │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │Topic         │  │ Follow-up    │  │ Calendar     │      │
│  │Classifier    │  │ Scheduler    │  │ Integrator   │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                          │
                          ▼ Output
┌─────────────────────────────────────────────────────────────┐
│                 Deliverables                                │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐      │
│  │Full      │ │Summary   │ │Actions   │ │Calendar │      │
│  │Transcript│ │Notes     │ │Items     │ │Events   │      │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘      │
└─────────────────────────────────────────────────────────────┘
```

## Workflow
1. Audio recording uploaded or streamed
2. Transcription agent converts speech to text
3. Summary agent creates condensed notes
4. Action item extractor identifies tasks and owners
5. Topic classifier tags discussion areas
6. Calendar integrator schedules follow-ups
7. All outputs delivered to user

## Tools
- **Whisper** or **AssemblyAI** for transcription
- **LangChain** or **CrewAI** for agent orchestration
- **Ollama** for local LLM processing
- **Google Calendar API** / **Outlook API**
- **Notion** or **Obsidian** for note storage
- **FastAPI** for service layer

## Learning Goals
- Multi-agent system design
- Speech-to-text processing
- Information extraction techniques
- API integration patterns

## Build Milestones
1. **Week 1**: Set up transcription pipeline
2. **Week 2**: Build summary generation agent
3. **Week 3**: Implement action item extraction
4. **Week 4**: Add topic classification
5. **Week 5**: Integrate calendar and notification
6. **Week 6**: Create unified dashboard and delivery
