# Project: Deep Learning Model Serving with TorchServe on Kubernetes

## Overview
Containerize a PyTorch vision model (ResNet-50) and serve it via TorchServe on Kubernetes. Implement autoscaling, health checks, canary deployments, and a REST API frontend for inference requests. Compare throughput against a baseline Flask-serving approach.

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│  Client (REST API caller)                          │
│  └── POST /predict  {image: base64}                │
├─────────────────────────────────────────────────────┤
│  Kubernetes Ingress (NGINX)                         │
│       │                                              │
│       ▼                                              │
│  ┌──────────────────────────────────────────────┐   │
│  │  KServ Deployment (TorchServe + Model)       │   │
│  │  Replicas: 2 (autoscaled to 5)               │   │
│  │  ├── torchserve:latest                       │   │
│  │  └── model.mar (ResNet-50 pretrained)        │   │
│  │                                               │   │
│  │  Readiness Probe: /ping                      │   │
│  │  Liveness Probe:  /models/resnet50/v1        │   │
│  └──────────────────────────────────────────────┘   │
│       │                                              │
│  ┌────▼────────────┐   ┌────────────────────────┐   │
│  │  Knative Serving │   │  HPA (CPU + custom)   │   │
│  │  (canary rollout)│   │  target: 50 req/s/pod  │   │
│  └─────────────────┘   └────────────────────────┘   │
├─────────────────────────────────────────────────────┤
│  Monitoring                                        │
│  ├── Prometheus metrics (/metrics endpoint)         │
│  └── Jaeger traces (inference latency per request)  │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Download and serialize a pre-trained ResNet-50 model to `.mar` format using TorchServe's `torch-model-archiver`
2. Write a Dockerfile based on `pytorch/torchserve` image
3. Create Kubernetes Deployment with liveness/readiness probes
4. Configure Horizontal Pod Autoscaler targeting inference throughput
5. Deploy a simple FastAPI wrapper that accepts images and proxies to TorchServe
6. Set up KNative or Argo Rollouts for canary deployment of updated model versions
7. Run benchmark with locust; compare TorchServe vs. Flask baseline
8. Visualize latency distributions and throughput in Grafana

## Tools
- **PyTorch** + **torchvision** (model training/saving)
- **TorchServe** (model serving framework)
- **Docker** (image packaging)
- **Kubernetes** (deployment, HPA, Ingress)
- **FastAPI** (inference API wrapper)
- **Locust** (performance benchmarking)
- **KNative** or **Argo Rollouts** (canary releases)

## Learning Goals
- Model serialization and TorchServe model archiving
- Kubernetes health probes for long-running inference services
- Autoscaling based on custom inference metrics
- Canary deployment strategies for ML models
- Performance benchmarking and latency profiling
- MLOps pipeline: train → archive → deploy → monitor

## Build Milestones
1. [ ] Save ResNet-50 as `.mar` using `torch-model-archiver`
2. [ ] Build and push Docker image to local registry
3. [ ] Deploy to minikube; verify `/ping` and model status endpoint
4. [ ] Add HPA targeting avg latency < 200ms
5. [ ] Build FastAPI proxy; test end-to-end inference
6. [ ] Implement canary deployment with KNative or Argo Rollouts
7. [ ] Run locust benchmark; capture p50/p95 latency
8. [ ] Compare throughput vs. baseline Flask approach

## References
- https://pytorch.org/serve/
- https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
