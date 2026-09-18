# Multi-Agent Meeting Assistant

## Overview
Create a multi-agent system that processes meeting transcripts, generates summaries, extracts action items, and schedules follow-ups. Agents collaborate: transcriber → summarizer → extractor → scheduler.

## Architecture
- **Multiple specialized agents** (transcriber, summarizer, extractor, scheduler)
- **Message passing** between agents
- **LLM orchestration** with LangGraph or custom framework
- **Calendar integration** for scheduling
- **Storage** for transcripts and outputs

## Workflow
1. Receive meeting audio/transcript input
2. Transcriber agent processes audio to text
3. Summarizer agent creates executive summary
4. Extractor agent identifies action items and decisions
5. Scheduler agent creates calendar events and tasks
6. Compile results into structured report

## Tools
- Python with LangGraph or custom agent framework
- Whisper/assemblyAI for transcription
- Ollama for local LLM inference
- Google Calendar API / Outlook API
- SQLite/PostgreSQL for storage
- FastAPI for API endpoints

## Learning Goals
- Multi-agent system design
- Agent collaboration patterns
- Workflow orchestration
- API integration for calendars
- Structured output parsing

## Build Milestones
1. Implement transcript ingestion pipeline
2. Build individual agent components
3. Create agent communication protocol
4. Integrate calendar API for scheduling
5. Design output report template
6. Add error handling and retries
7. Build web interface for submission

---
*Generated: 2026-09-18 | Source: AI overnight research engine*
