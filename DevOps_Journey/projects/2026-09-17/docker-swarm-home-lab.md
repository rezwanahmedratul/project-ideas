# Docker Swarm Home Lab Infrastructure

## Overview
Deploy a production-like Docker Swarm cluster at home for learning container orchestration, service discovery, and high availability patterns without cloud costs.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                    Docker Swarm Cluster                     │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │  Manager    │  │  Worker     │  │  Worker     │        │
│  │  Node 1     │  │  Node 2     │  │  Node 3     │        │
│  │  (etcd)     │  │             │  │             │        │
│  └─────────────┘  └─────────────┘  └─────────────┘        │
└─────────────────────────────────────────────────────────────┘
                          │
          ┌───────────────┼───────────────┐
          ▼               ▼               ▼
   ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
   │  Services   │ │  Secrets    │ │  Configs    │
   │  Stack      │ │  Management │ │  Store      │
   └─────────────┘ └─────────────┘ └─────────────┘
```

## Services to Deploy
- **Traefik**: Reverse proxy and load balancer
- **Portainer**: Container management UI
- **Prometheus + Grafana**: Monitoring stack
- **Longhorn**: Distributed block storage
- **Registry**: Private Docker image registry
- **Jenkins**: CI/CD automation
- **Gitea**: Git repository hosting

## Workflow
1. Provision 3+ machines (physical or VMs)
2. Install Docker on each node
3. Initialize Swarm manager on first node
4. Join worker nodes to cluster
5. Deploy services via docker-compose stacks
6. Configure storage and networking
7. Set up monitoring and backups

## Tools
- **Docker Swarm** for orchestration
- **Linux** (Ubuntu/Debian) as host OS
- **Traefik** for routing
- **Prometheus** + **Grafana** for monitoring
- **Longhorn** for persistent storage
- **Ansible** for automated deployment

## Learning Goals
- Container orchestration fundamentals
- Service discovery and load balancing
- Persistent storage in distributed systems
- High availability patterns

## Build Milestones
1. **Week 1**: Provision nodes and install Docker
2. **Week 2**: Initialize Swarm cluster
3. **Week 3**: Deploy Traefik and Portainer
4. **Week 4**: Set up Longhorn storage
5. **Week 5**: Deploy monitoring stack
6. **Week 6**: Add CI/CD and test failover
