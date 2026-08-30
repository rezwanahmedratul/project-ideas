# Homelab MCP Server for AI Agents

## Overview
A Model Context Protocol (MCP) server that exposes homelab infrastructure as tools for AI agents. Enables ChatGPT, Claude, or other LLM clients to query and control your home infrastructure through standardized MCP tool calls.

## Architecture / Structure
- **MCP Server Core**: Implements MCP protocol over stdio or SSE
- **Tool Registry**: Exposes homelab operations as discoverable tools
- **Auth Layer**: Validates requests and enforces permission scopes
- **Infrastructure Adapters**: Connectors for Proxmox, Kubernetes, Docker, OpenHAB
- **Query Router**: Routes tool calls to appropriate infrastructure backend
- **Audit Logger**: Records all agent interactions for security review

## Tools Exposed
- `get_proxmox_status`: List VMs/CTs and resource usage
- `start_vm`: Power on a virtual machine
- `get_k8s_pods`: List pods by namespace with status
- `scale_deployment`: Adjust replica count for a deployment
- `check_storage`: Volume usage and growth trends
- `restart_service`: Restart a docker container or systemd service
- `run_compose`: Execute docker-compose commands safely

## Workflow
1. Configure MCP server with homelab credentials and allowed operations
2. AI agent connects via MCP client (ChatGPT custom, Claude Desktop, etc.)
3. Agent discovers available tools through MCP protocol
4. User asks "what's my CPU usage?" → agent calls get_proxmox_status
5. Server validates request scope and executes safely
6. Result returned to agent with formatted context
7. All actions logged to audit trail

## Tools
- MCP SDK (TypeScript or Python)
- Proxmox VE API (pveproxy)
- Kubernetes Python client
- Docker SDK for Python
- FastAPI for optional HTTP endpoint
- SQLite for audit logging

## Learning Goals
- MCP protocol specification and implementation
- Infrastructure API integration patterns
- Tool design for AI agents
- Security considerations for AI-controlled systems
- Multi-service orchestration

## Build Milestones
1. Week 1: MCP server skeleton with stdio transport
2. Week 2: Proxmox API integration and VM status tool
3. Week 3: Kubernetes pod listing and scaling tools
4. Week 4: Docker container management tools
5. Week 5: Authentication and permission scoping
6. Week 6: Audit logging and integration testing with AI clients
