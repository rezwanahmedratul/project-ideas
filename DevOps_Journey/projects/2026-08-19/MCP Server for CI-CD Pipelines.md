# MCP Server for CI/CD Pipelines

**Category:** Combined (DevOps + AI/ML)  
**Date:** 2026-08-19  
**Difficulty:** Intermediate  

## Overview
A **Model Context Protocol (MCP) server** that exposes your CI/CD system (GitHub Actions, GitLab CI, or Jenkins) to AI coding agents as tools. Agents can query pipeline status, fetch failed-job logs, trigger re-runs, and read deployment state — securely and read-mostly by default. This connects the autonomous-coding-agent world (today's dev report) with real pipeline control, behind a permission boundary.

## Architecture / Structure
```
cicd-mcp/
├── server.py            # MCP server (FastMCP / official SDK)
├── tools/
│   ├── get_pipeline_status.py
│   ├── get_job_logs.py
│   ├── trigger_pipeline.py   # gated
│   └── list_deployments.py
├── providers/
│   ├── github_actions.py
│   └── gitlab_ci.py
├── config.yaml          # tokens, allowed actions, dry-run
└── README.md
```

## Workflow
1. An MCP-compatible agent connects to the server.
2. It lists available tools (status, logs, deployments) and calls them.
3. Read actions return JSON; mutating actions (re-run, deploy) require explicit allowlist + confirmation.
4. All calls are audited to a log for review.
5. The agent uses results to explain or fix a broken pipeline (links to the CI Failure Explainer pattern).

## Tools
- Python, official MCP SDK / FastMCP
- GitHub/GitLab/Jenkins REST APIs
- `pydantic` for tool schemas
- Docker for deployment; audit log to file/SQLite

## Learning Goals
- The Model Context Protocol and agent-tool integration.
- Securely exposing infrastructure APIs to agents.
- Designing read-only-by-default tool surfaces.
- Auditability of agent actions.

## Build Milestones
1. Stand up an MCP server exposing `get_pipeline_status`.
2. Add `get_job_logs` + `list_deployments` for one provider.
3. Add gated mutating tools with an allowlist + confirmation.
4. Implement the audit log and a dry-run mode.
5. Connect a coding agent (Claude Code / Cline) and resolve a real failed run via the server.
