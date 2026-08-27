# Homelab MCP Server for AI Agents

**Date:** 2026-08-27
**Category:** Combined (DevOps + AI)
**Tags:** mcp, homelab, home-assistant, automation, anthropic

---

## Overview

Build a Model Context Protocol (MCP) server that exposes your entire homelab as tools an AI assistant can use. Ask Claude or any MCP-compatible client to check server status, deploy services, read logs, or restart containers — all through natural language.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│              MCP Client (Claude, ChatGPT, etc.)             │
│  "Check if my Proxmox host is healthy"                      │
│  "Deploy nextcloud to my k8s cluster"                       │
│  "What's the CPU usage on NAS?"                             │
└─────────────────────────────┬───────────────────────────────┘
                              │ MCP Protocol (JSON-RPC)
                              ▼
┌─────────────────────────────────────────────────────────────┐
│              Homelab MCP Server                              │
│                                                             │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐  │
│  │  Proxmox     │  │  Kubernetes  │  │  Home Assistant  │  │
│  │  Tools       │  │  Tools       │  │  Tools           │  │
│  └──────────────┘  └──────────────┘  └──────────────────┘  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐  │
│  │  Docker      │  │  Network     │  │  Monitoring      │  │
│  │  Tools       │  │  Tools       │  │  Tools           │  │
│  └──────────────┘  └──────────────┘  └──────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                    Homelab Infrastructure                    │
│  Proxmox │ Kubernetes │ Docker │ Home Assistant │ SNMP     │
└─────────────────────────────────────────────────────────────┘
```

## Tool Categories

### Infrastructure Tools
| Tool | Description | Safety |
|------|-------------|--------|
| `proxmox_node_status` | Get cluster/node health | Read-only |
| `proxmox_vm_list` | List VMs with resources | Read-only |
| `proxmox_vm_start` | Start a VM | Write (approved) |
| `proxmox_vm_shutdown` | Graceful shutdown | Write (approved) |

### Kubernetes Tools
| Tool | Description | Safety |
|------|-------------|--------|
| `k8s_pods` | List pods by namespace | Read-only |
| `k8s_logs` | Stream pod logs | Read-only |
| `k8s_deploy` | Apply manifest from URL/Git | Write (approved) |
| `k8s_scale` | Scale deployment | Write (approved) |

### Home Automation Tools
| Tool | Description | Safety |
|------|-------------|--------|
| `ha_devices` | List all devices/entities | Read-only |
| `ha_state` | Get entity state | Read-only |
| `ha_call_service` | Trigger automation | Write (approved) |

### Monitoring Tools
| Tool | Description | Safety |
|------|-------------|--------|
| `prometheus_query` | Execute PromQL query | Read-only |
| `grafana_dashboard` | Return dashboard screenshot URL | Read-only |
| `alertmanager_status` | List firing alerts | Read-only |

## MCP Server Implementation

```python
# Simplified MCP server structure
from mcp.server import Server
import httpx

app = Server("homelab-mcp")

@app.tool()
async def get_node_health(node: str) -> str:
    """Get health status of a Proxmox node."""
    async with httpx.AsyncClient() as client:
        response = await client.get(
            f"https://{node}:8006/api2/json/nodes/{node}/status",
            headers={"Authorization": f"PVEAPIToken={API_TOKEN}"},
            verify=False
        )
        return json.dumps(response.json())

@app.tool()
async def k8s_get_pods(namespace: str, label: str = None) -> str:
    """List Kubernetes pods in a namespace."""
    # ... implementation using kubectl subprocess or kubernetes python client
```

## Security Considerations

1. **Token-scoped API access** — Use minimal-permission API tokens
2. **Whitelist approved tools** — Not all tools should be callable by AI
3. **Write action approval** — Require confirmation for destructive operations
4. **Audit logging** — Log all AI-initiated actions with timestamps
5. **Network isolation** — MCP server only accessible from trusted network

## Integration Setup

### Claude Desktop
```json
{
  "mcpServers": {
    "homelab": {
      "command": "python3",
      "args": ["/opt/mcp/homelab_server.py"],
      "env": {
        "PROXMOX_URL": "https://proxmox.local:8006",
        "KUBECONFIG": "/root/.kube/config",
        "HA_URL": "http://homeassistant:8123"
      }
    }
  }
}
```

### VS Code / Cursor
Same configuration in extension settings.

## Learning Goals

- MCP protocol specification and implementation
- API integration patterns (REST, authenticated)
- Tool design principles (idempotency, safety)
- Home lab networking and security
- AI-assisted operations workflows

## Build Milestones

1. [ ] Set up MCP server project structure
2. [ ] Implement Proxmox read-only tools
3. [ ] Implement Kubernetes read-only tools
4. [ ] Add Home Assistant integration
5. [ ] Build Prometheus/Grafana query tools
6. [ ] Implement write tools with approval gate
7. [ ] Add audit logging and access controls
8. [ ] Create documentation and example prompts
9. [ ] Deploy and test with Claude Desktop

---
*Generated: 2026-08-27*
