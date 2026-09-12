# Kubernetes GitOps Dashboard

## Overview
Build a real-time dashboard that visualizes Kubernetes cluster state through a GitOps lens, showing the diff between desired state (Git) and actual state (cluster).

## Architecture
- Frontend: React with K8s resource visualization
- Backend: Go API server communicating with Kubernetes API
- Data source: ArgoCD/Flux sync status + kubectl get diffs
- Database: SQLite for caching recent states

## Workflow
1. Connect to Kubernetes cluster via kubeconfig
2. Fetch all GitOps-managed applications from ArgoCD
3. Compute drift between Git manifests and live cluster state
4. Display real-time sync status with visual indicators
5. Show detailed diff on click for troubleshooting

## Tools
- Kubernetes API, ArgoCD CLI, Go, React, WebSocket

## Learning Goals
- GitOps principles and implementation
- Kubernetes custom resources and operators
- Real-time data streaming with WebSockets
- Infrastructure state management

## Build Milestones
1. Basic cluster connection and resource listing
2. ArgoCD integration and sync status display
3. Diff computation engine
4. Real-time updates and alerts
5. Export and reporting features
