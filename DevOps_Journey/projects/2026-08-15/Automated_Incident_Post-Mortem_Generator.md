# Automated Incident Post-Mortem Generator

**Category:** Combined
**Suggested Date:** 2026-08-15
**Status:** Idea / Not Started

## Overview
A tool that ingests incident timelines from chat logs, PagerDuty tickets, Prometheus alerts, and K8s events, then generates a structured post-mortem document with root cause hypothesis and action items.

## What It Will Do
- Solve a practical problem related to combined.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
postmortem-generator/
├── README.md
├── sources/
│   ├── slack_ingestor.py
│   ├── pagerduty_client.py
│   └── prometheus_fetcher.py
├── timeline_builder/
├── llm_writer/
│   └── postmortem_generator.py
├── templates/
├── api/
├── ui/
└── tests/

## How It Will Work
1. Define the core use case and minimal working workflow.
2. Build the API/automation pipeline first.
3. Add persistence, observability, and error handling.
4. Containerize the application and add CI.
5. Write documentation and create a demo scenario.

## Tools / Tech Stack
Slack/Telegram API, PagerDuty API, Prometheus Loki, Kubernetes events, FastAPI, Ollama/local LLM, LangChain, SQLite, React markdown editor

## Learning Goals
Learn incident management workflows, multi-source data aggregation, timeline reconstruction, AI-assisted writing, and reliability engineering documentation standards.

## Build Milestones
- **MVP:** Feed a simulated incident timeline to an LLM and get a structured markdown report.
- **v1:** Connect real PagerDuty and Slack channels to auto-collect incident data.
- **v2:** Add cross-incident pattern analysis and recurring issue heatmaps.
- **Portfolio polish:** Template library, real incident anonymized example, tool demo.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
