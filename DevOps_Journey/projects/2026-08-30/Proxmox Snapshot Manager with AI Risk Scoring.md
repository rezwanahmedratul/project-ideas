# Proxmox Snapshot Manager with AI Risk Scoring

## Overview
An intelligent snapshot management system for Proxmox VE that evaluates VM workload patterns and creates optimal backup schedules. AI analysis predicts which VMs need frequent snapshots vs long intervals based on change rate and criticality.

## Architecture / Structure
- **Workload Profiler**: Monitors disk write patterns and state change frequency per VM
- **Risk Assessor**: Calculates snapshot necessity score based on VM criticality + change rate
- **Scheduler**: Creates cron jobs for optimal snapshot windows avoiding peak usage
- **Retention Policy Engine**: Applies tiered retention (hot/warm/cold storage)
- **Restore Orchestrator**: Fast VM restoration from point-in-time snapshots

## Workflow
1. Profile each VM's IOPS pattern over 7 days baseline
2. Classify VMs: database (high change), web server (medium), static (low)
3. Generate snapshot schedule: high-risk VMs every hour, low-risk daily
4. Execute snapshots during low-I/O windows
5. Compress and deduplicate across similar VM states
6. Alert on storage capacity trends

## Tools
- Proxmox VE API (REST)
- Python with proxmoxer library
- SQLite for metadata storage
- Prometheus node_exporter for monitoring
- Telegram webhook for alerts

## Learning Goals
- Proxmox VE architecture and API
- Storage optimization techniques for VM snapshots
- Predictive scheduling algorithms
- Backup strategy design for virtualization platforms

## Build Milestones
1. Week 1: Proxmox API connection and VM inventory
2. Week 2: Baseline IOPS collection and storage in SQLite
3. Week 3: Simple rule-based classification of VMs
4. Week 4: Automated snapshot creation with policy engine
5. Week 5: Deduplication and compression strategy
6. Week 6: Restore testing and alerting integration
