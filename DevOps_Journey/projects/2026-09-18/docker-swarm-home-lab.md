# Docker Swarm Home Lab Infrastructure

## Overview
Build a production-grade Docker Swarm cluster on Proxmox VMs with persistent storage, overlay networking, Traefik routing, and automated backup/restore procedures for self-hosted services.

## Architecture
- **Proxmox VE** for VM hosting
- **Docker Swarm** for container orchestration
- **Traefik** as reverse proxy and load balancer
- **Longhorn/Ceph** for distributed storage
- **Cockpit** for cluster management UI
- **Automated backups** with restic/kdump

## Workflow
1. Provision VMs on Proxmox (manager + workers)
2. Initialize Docker Swarm with managers and workers
3. Configure overlay networking across nodes
4. Deploy Traefik for ingress routing
5. Deploy services with persistent volumes
6. Set up monitoring (Prometheus/Grafana/Pushgateway)
7. Configure automated backups and restore procedures

## Tools
- Proxmox VE
- Docker Engine + Docker Swarm
- Traefik (reverse proxy/load balancer)
- Longhorn (distributed block storage)
- Prometheus + Grafana + Node Exporter
- Restic or BorgBackup for backups
- Cockpit for management UI

## Learning Goals
- Docker Swarm vs Kubernetes comparison
- Container networking and overlay networks
- Storage drivers and persistent volumes
- Reverse proxy configuration
- Backup and disaster recovery strategies

## Build Milestones
1. Provision 3 Proxmox VMs (1 manager, 2 workers)
2. Install and initialize Docker Swarm
3. Configure overlay networking
4. Deploy Traefik with HTTPS termination
5. Create service stack (monitoring, storage, apps)
6. Set up automated backups
7. Test failover and disaster recovery

---
*Generated: 2026-09-18 | Source: AI overnight research engine*
