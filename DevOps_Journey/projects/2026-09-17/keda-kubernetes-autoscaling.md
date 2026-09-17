# Kubernetes-Native Auto-Scaling with KEDA

## Overview
Implement event-driven auto-scaling for Kubernetes workloads using KEDA (Kubernetes Event-Driven Autoscaling), scaling pods based on external metrics like queue depth, HTTP requests, or custom metrics.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                    Kubernetes Cluster                        │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  KEDA Scaler                                       │  │
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐   │  │
│  │  │ Kafka   │ │ Prometheus│ │ HTTP    │ │ Custom  │   │  │
│  │  │ Scaled  │ │ Scaled   │ │ Scaled  │ │ Metric  │   │  │
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────┘   │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                          │
                          ▼ Scale
┌─────────────────────────────────────────────────────────────┐
│                 Workload Deployment                         │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  ReplicaSet / Deployment                             │  │
│  │  (HPA managed by KEDA)                               │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

## Supported Scalers
- **Kafka**: Scale based on consumer lag
- **Prometheus**: Scale based on any metric
- **HTTP**: Scale based on concurrent requests
- **Redis**: Scale based on queue length
- **Custom**: Scale based on any REST endpoint

## Workflow
1. Define ScaledObject with scaler configuration
2. KEDA watches scaler metrics continuously
3. Calculate desired replica count from metric value
4. Update HorizontalPodAutoscaler (HPA) targets
5. K8s scheduler adjusts pod count
6. Scale-down after cooldown period

## Tools
- **KEDA** operator
- **Kubernetes** 1.28+
- **Prometheus** for metrics
- **Kafka** / **RabbitMQ** for event streams
- **Helm** for deployment
- **kubectl** for management

## Learning Goals
- Event-driven architecture patterns
- Kubernetes HPA configuration
- External metrics integration
- Auto-scaling best practices

## Build Milestones
1. **Week 1**: Set up Kubernetes cluster with metrics server
2. **Week 2**: Install KEDA operator
3. **Week 3**: Deploy sample app with Kafka scaler
4. **Week 4**: Configure Prometheus scaler
5. **Week 5**: Add HTTP scaler for web app
6. **Week 6**: Test scale-up/down scenarios and optimize
