# Homelab MCP Server with Proxmox Integration

## Overview
Create an MCP (Model Context Protocol) server that exposes homelab operations (VM status, storage, networking) to AI assistants like Claude, allowing natural language management.

## Architecture
```
AI Client (Claude/Cursor/etc.)
    ↓
MCP Client Library
    ↓
Homelab MCP Server
    ↓
Proxmox API
    ↓
VMs / Containers / Storage / Network
```

## Workflow
1. Implement MCP server specification in Python/TypeScript
2. Expose tools: list_vms, get_vm_status, start_vm, stop_vm
3. Add storage tools: list_pools, check_usage
4. Add network tools: list_bridges, show_firewall
5. Test with Claude desktop or Cursor
6. Add authentication for Proxmox API

## Tools
- Python or TypeScript
- mcp-sdk or python-mcp
- proxmoxer library
- FastAPI for HTTP endpoint

## Learning Goals
- Model Context Protocol specification
- AI agent tool integration
- Proxmox API fundamentals
- Secure credential management

## Build Milestones
- [ ] Set up MCP server skeleton
- [ ] Implement VM management tools
- [ ] Add storage monitoring tools
- [ ] Create network inspection tools
- [ ] Test with Claude Desktop
- [ ] Add auth and rate limiting

## References
- https://modelcontextprotocol.io/
- https://pypi.org/project/proxmoxer/
- https://pve.proxmox.com/wiki/REST_API
