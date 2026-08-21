# AI Kubernetes Incident Response Copilot

## Overview
An AI-powered copilot that analyzes Kubernetes incidents in real-time, correlates logs and metrics, suggests root causes, and guides remediation — all within the terminal or IDE.

## Architecture
```
┌─────────────────────────────────────────────────┐
│           Kubernetes Cluster                    │
│  ┌─────────┐  ┌─────────┐  ┌─────────┐        │
│  │ Pods    │  │ Services│  │ Nodes   │        │
│  └────┬────┘  └────┬────┘  └────┬────┘        │
└───────┼────────────┼────────────┼──────────────┘
        │            │            │
   ┌────▼────┐ ┌────▼────┐ ┌────▼────┐
   │ Metrics │ │ Logs    │ │ Events  │
   │(Prometheus)│(Loki) │ │(k8s)    │
   └────┬────┘ └────┬────┘ └────┬────┘
        └────────────┼────────────┘
                     ▼
          ┌─────────────────────┐
          │  Incident           │
          │  Correlator         │
          │  (AI Agent)         │
          └──────────┬──────────┘
                     │
          ┌──────────▼──────────┐
          │  Response           │
          │  Suggestions        │
          │  (Terminal/IDE)     │
          └─────────────────────┘
```

## Workflow
1. Alert fires (OOMKilled, CrashLoopBackOff, etc.)
2. Copilot collects relevant context automatically
3. LLM analyzes patterns across logs/metrics/events
4. Presents probable root cause with evidence
5. Offers remediation commands with explanations
6. Optional: apply fix with human confirmation

## Tools
- **Prometheus** + **Grafana** for metrics
- **Loki** + **Promtail** for logs
- **kubectl** for cluster interaction
- **Ollama** for local LLM (privacy)
- **Python** for orchestration

## Learning Goals
- Kubernetes failure modes and diagnostics
- Log correlation and observability
- AI-assisted SRE workflows
- Incident response automation

## Build Milestones
1. [ ] Alert ingestion from Prometheus alerts
2. [ ] Context collection (logs, metrics, events)
3. [ ] LLM-based root cause analysis
4. [ ] Remediation suggestion engine
5. [ ] Terminal copilot interface
6. [ ] IDE extension (VS Code)
7. [ ] Post-incident report generation
