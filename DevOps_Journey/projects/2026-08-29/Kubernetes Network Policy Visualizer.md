# Kubernetes Network Policy Visualizer

## Overview
Kubernetes network policies are powerful but opaque. This tool visualizes allowed/denied traffic flows between pods, services, and namespaces in real-time, making it easier to debug connectivity issues and audit security postures.

## Architecture / Structure
- **Data Collector**: Sidecar or daemonset scraping network policy rules and actual connection logs
- **Graph Engine**: Builds a directed graph of pod-to-pod communication paths
- **Visualizer**: Force-directed or hierarchical graph rendered in a web UI
- **Policy Analyzer**: Identifies overly permissive or conflicting policies

## Workflow
1. Deploy collector as a daemonset across the cluster
2. Collect Cilium/network-policy audit logs and policy definitions
3. Build adjacency matrix of allowed traffic flows
4. Render interactive network map with color-coded risk levels
5. Highlight violations and suggest tighter policies

## Tools
- Kubernetes Network Policy API
- Cilium Hubble (for flow visibility)
- D3.js or vis.js for graph visualization
- Go backend for Kubernetes client interaction
- Helm chart for deployment

## Learning Goals
- Deep understanding of Kubernetes networking layers
- Network policy semantics and enforcement mechanisms
- Graph visualization techniques
- Security auditing and compliance visualization

## Build Milestones
1. Week 1: Kubernetes network policy CRUD operations + list API
2. Week 2: Cilium Hubble flow integration
3. Week 3: Graph data structure and REST API
4. Week 4: Web visualization with D3.js force layout
5. Week 5: Risk scoring and policy violation detection
6. Week 6: Helm chart packaging and documentation
