# LLM-Powered Log Investigator with RCA

**Category:** Combined (DevOps + AI/ML)  
**Date:** 2026-08-19  
**Difficulty:** Advanced  

## Overview
An AI assistant that ingests application and system logs, performs **root-cause analysis (RCA)**, and explains incidents in plain language. Unlike a pure log-anomaly detector, it correlates across services using RAG over your runbooks + past incidents, then proposes likely causes and remediation steps. A natural evolution of the earlier "Real-time Log Anomaly Detector" idea, but with reasoning and historical context.

## Architecture / Structure
```
log-investigator/
├── collector/            # tail/fetch logs -> normalize
├── vectorstore/          # embeddings of logs + runbooks (Chroma)
├── rag/                  # retrieval + prompt construction
├── llm/                  # local or API model interface
├── api/                  # FastAPI: POST incident -> RCA report
├── ui/                   # minimal chat/report page
├── deploy/              # docker-compose
└── README.md
```

## Workflow
1. Logs stream in (Loki/Promtail or file tail) and get embedded into a vector store.
2. On an alert or manual query, the system retrieves relevant recent logs + matching past incidents/runbooks.
3. An LLM synthesizes a root-cause hypothesis, evidence, and suggested fixes.
4. Output is a structured RCA report (what, why, fix, confidence) pushed to the notifier service.

## Tools
- Python, FastAPI, Loki/Promtail or file tail
- Chroma / Qdrant vector DB, sentence-transformers
- Local LLM (llama.cpp) or API; Grafana for context
- Docker Compose

## Learning Goals
- RAG over semi-structured operational data.
- Log normalization and embedding pipelines.
- Combining observability with LLM reasoning.
- Producing explainable, cited AI output (grounding).

## Build Milestones
1. Collect + normalize logs and store embeddings in Chroma.
2. Build a retrieval query from an alert and feed to an LLM for RCA.
3. Add a runbook/incident-history corpus to retrieval.
4. Produce a structured RCA report + confidence score.
5. Wire to the notifier service and a minimal UI; test on a past incident.
