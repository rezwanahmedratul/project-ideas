# Project: Docker Swarm Home Lab Infrastructure

## Overview
Deploy a self-hosted home lab using Docker Swarm orchestration with reverse proxy, monitoring, and automated backups. Simulates production-like infrastructure on affordable hardware.

## Architecture
```
┌────────────────────────────────────────────────────────────┐
│  Docker Swarm Cluster (3 nodes: 1 manager, 2 workers)      │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  Ingress / Reverse Proxy                           │   │
│  │  (Caddy + Traefik)                                  │   │
│  │  • TLS termination                                  │   │
│  │  • Host-based routing                               │   │
│  └──────────────────┬──────────────────────────────────┘   │
│                     │                                      │
│    ┌────────────────┼────────────────┐                     │
│    ▼                ▼                ▼                     │
│ ┌──────┐      ┌──────────┐      ┌──────────┐              │
│ │Portainer│     │Watchtower│     │  Uptime │              │
│ │(mgmt)  │      │(auto-pull)│     │ Kuma    │              │
│ └──────┘      └──────────┘      └──────────┘              │
│                                                            │
│  ┌──────────┐   ┌──────────┐   ┌──────────┐              │
│  │  Gitea   │   │  Nextcloud│   │  Filebrowser│            │
│  │(Git)     │   │(files)    │   │(files)     │             │
│  └──────────┘   └──────────┘   └──────────┘              │
│                                                            │
│  ┌──────────┐   ┌──────────┐   ┌──────────┐              │
│  │  Grafana │   │  Prometheus│   │  Loki   │              │
│  │          │   │           │   │          │              │
│  └──────────┘   └──────────┘   └──────────┘              │
└────────────────────────────────────────────────────────────┘
```

## Workflow
1. Provision 2-3 Raspberry Pi 4/5 or old laptops
2. Install Docker and initialize Swarm mode
3. Deploy stack files for each service
4. Configure Caddy as ingress with TLS
5. Set up Watchtower for auto-updates
6. Deploy monitoring stack
7. Configure backup cron jobs

## Tools & Tech Stack
- **Docker Swarm** — Container orchestration
- **Caddy** — Reverse proxy + TLS
- **Traefik** — Alternative ingress controller
- **Portainer** — Visual management UI
- **Watchtower** — Automatic container updates
- **Uptime Kuma** — Health monitoring
- **Grafana/Prometheus/Loki** — Observability
- **Gitea** — Self-hosted Git
- **Nextcloud** — File storage and sync

## Learning Goals
- Docker Swarm vs Kubernetes trade-offs
- Service discovery in container orchestration
- Docker Compose for production deployments
- Reverse proxy configuration
- TLS certificate management (Let's Encrypt)
- Hardware-efficient container hosting

## Build Milestones
1. [ ] Flash OS and install Docker on nodes
2. [ ] Initialize Swarm and join workers
3. [ ] Deploy Caddy with TLS
4. [ ] Create docker-compose stacks for services
5. [ ] Set up monitoring (Prometheus stack)
6. [ ] Configure automated backups
7. [ ] Document infrastructure and create runbooks

## Reference Links
- [Docker Swarm Documentation](https://docs.docker.com/engine/swarm/)
- [Caddy Server](https://caddyserver.com/)
- [Awesome Docker Selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted)
