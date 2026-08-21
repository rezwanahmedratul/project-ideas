# Homelab MCP Server for AI Agents

## Overview
A Model Context Protocol (MCP) server exposing homelab resources (Proxmox VMs, Docker services, network info) to AI agents via a standardized interface.

## Architecture
```
┌─────────────────────────────────────────────────┐
│           AI Agent (Claude, etc.)               │
│  ┌─────────────────────────────────────────┐    │
│  │ "Check if my web server is running"     │    │
│  └──────────────────┬──────────────────────┘    │
└─────────────────────┼───────────────────────────┘
                      │ MCP Protocol
                      ▼
          ┌────────────────────────┐
          │  MCP Server            │
          │  (Python/FastMCP)      │
          └───────────┬────────────┘
                      │
        ┌─────────────┼─────────────┐
        ▼             ▼             ▼
  ┌──────────┐  ┌──────────┐  ┌──────────┐
  │ Proxmox  │  │ Docker   │  │ Network  │
  │ API      │  │ API      │  │ Tools    │
  └──────────┘  └──────────┘  └──────────┘
```

## Tools Exposed

| Tool | Description | Example Use |
|------|-------------|-------------|
| `proxmox_list_vms` | List all VMs with status | "Which VMs are running?" |
| `docker_ps` | Container status | "Is my web server up?" |
| `ping_host` | Connectivity check | "Can I reach the gateway?" |
| `prometheus_query` | Metric queries | "What's CPU usage?" |
| `kubectl_get` | K8s resource checks | "Any pods crashing?" |
| `uptime_check` | Service availability | "Is the backup working?" |

## Tools
- **FastMCP** (Python MCP SDK)
- **Proxmox VE API** (REST)
- **Docker SDK for Python**
- **Prometheus HTTP API**
- **Python async** for concurrent queries

## Learning Goals
- MCP protocol specification
- Tool design for AI agents
- API integration patterns
- Security and permission scoping

## Build Milestones
1. [ ] MCP server skeleton with FastMCP
2. [ ] Proxmox VM listing tool
3. [ ] Docker container status tool
4. [ ] Prometheus metrics query tool
5. [ ] Security: tool permission scopes
6. [ ] Claude Desktop integration test
7. [ ] Documentation and example prompts
