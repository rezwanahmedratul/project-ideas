# Project: Kubernetes Auto-Scaler for Variable Workloads

## Overview
Build a custom Kubernetes Horizontal Pod Autoscaler (HPA) controller that scales deployments based on custom metrics (e.g., queue depth, message count, custom API latency). Deploy to a minikube cluster and demonstrate scaling behavior under simulated load.

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│  Kubernetes Cluster (minikube)                      │
│  ┌───────────────────────────────────────────────┐  │
│  │  Custom Metrics Adapter (prometheus-adapter)  │  │
│  │  └── exposes custom metrics to HPA            │  │
│  └───────────────────────────────────────────────┘  │
│                                                         │
│  ┌───────────────────────────────────────────────┐    │
│  │  MyWebApp Deployment                          │    │
│  │  Replicas: 1 → 5 (scaled by HPA)             │    │
│  │  Metric: requests/second (from nginx-log)      │    │
│  └───────────────────────────────────────────────┘    │
│                                                         │
│  ┌───────────────────────────────────────────────┐    │
│  │  Job Generator (load test script)              │    │
│  │  Simulates traffic spikes                      │    │
│  └───────────────────────────────────────────────┘    │
├─────────────────────────────────────────────────────┤
│  External System                                     │
│  ├── RabbitMQ (queue depth metric)                   │
│  └── Custom Golang metrics exporter                  │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Start minikube with metrics-server addon enabled
2. Deploy a sample Python/Flask web app with 1 replica
3. Install **prometheus-adapter** to expose custom metrics
4. Write a **Sidecar container** or **metrics exporter** that reports request rate to Prometheus
5. Create a `CustomMetric` object mapping the app metric to Prometheus format
6. Create HPA YAML targeting the deployment by custom metric (target 50 req/s per pod)
7. Run a load test using `fortio` or `k6` to simulate traffic spikes
8. Observe scaling up/down events via `kubectl get hpa --watch` and `kubectl describe hpa`

## Tools
- **minikube** (local Kubernetes cluster)
- **kubectl** (cluster management)
- **prometheus-adapter** (custom metrics → HPA)
- **Python Flask** or **Go (httptest)** (sample app)
- **k6** or **Fortio** (load testing)
- **Prometheus** (metrics collection)

## Learning Goals
- Kubernetes HPA mechanics and metric types (CPU, memory, custom)
- Custom metrics adapter configuration
- Sidecar pattern for exposing application-specific metrics
- Load testing methodologies for autoscaling validation
- HPA behavior: scale-up thresholds, stabilization windows, scale-down delay
- Debugging failed scaling with `kubectl describe hpa`

## Build Milestones
1. [ ] Start minikube; verify metrics-server is running
2. [ ] Deploy sample app; confirm basic CPU-based HPA works
3. [ ] Add metrics exporter sidecar exposing request rate
4. [ ] Install prometheus-adapter; map custom metric
5. [ ] Create HPA manifest targeting custom metric at 50 req/s
6. [ ] Run k6 load test; observe scale-up behavior
7. [ ] Tune HPA parameters (minReplicas, maxReplicas, stabilization window)
8. [ ] Capture and analyze scale events with kubectl describe hpa

## References
- https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/
- https://github.com/kubernetes-sigs/custom-metrics-apiserver
