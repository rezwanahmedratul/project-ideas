# Project: Proxmox Home Lab with Automated Backups

## Overview
Build a complete Proxmox virtualization lab with automated VM backups, snapshot management, and monitoring. This project covers KVM virtualization, LXC containers, network storage, and disaster recovery procedures.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                     Proxmox Host                            │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │  VM: Ubuntu │  │  VM: Debian │  │ LXC:nginx   │        │
│  │  (KVM)      │  │  (KVM)      │  │ (LXC)       │        │
│  │             │  │             │  │             │        │
│  │ Docker      │  │ Prometheus  │  │ Monitoring  │        │
│  │ MinIO S3    │  │ Grafana     │  │ Alertmanager│        │
│  └─────────────┘  └─────────────┘  └─────────────┘        │
│  ┌─────────────┐  ┌─────────────┐                         │
│  │ LXC: GitLab │  │ LXC:NAS     │                         │
│  │ (CI/CD)     │  │ (ZFS Storage)│                         │
│  └─────────────┘  └─────────────┘                         │
├─────────────────────────────────────────────────────────────┤
│  ZFS Pool: Data + Backup Storage                           │
│  Network: Bridge → Physical NIC                           │
└─────────────────────────────────────────────────────────────┘
```

## Workflow
1. Install Proxmox VE on bare metal or VM
2. Configure ZFS storage pool
3. Create LXC containers for services
4. Set up VMs for Windows/Linux workloads
5. Configure automated backup jobs
6. Implement snapshot schedules
7. Set up offsite replication
8. Monitor with Prometheus/Grafana

## Tools
- Proxmox VE
- ZFS
- LXC containers
- QEMU/KVM
- rsync / borgbackup
- Prometheus + node_exporter

## Learning Goals
- KVM vs LXC virtualization tradeoffs
- ZFS filesystem management
- Backup strategy design (3-2-1 rule)
- Resource allocation and quotas
- Disaster recovery procedures

## Build Milestones
- [ ] Week 1: Proxmox installation and configuration
- [ ] Week 2: ZFS storage setup
- [ ] Week 3: Create first LXC containers
- [ ] Week 4: Set up VMs
- [ ] Week 5: Configure networking
- [ ] Week 6: Implement backup automation
- [ ] Week 7: Set up monitoring
- [ ] Week 8: Test restore procedures
