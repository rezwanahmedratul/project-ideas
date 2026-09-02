# Project: Go Microservices with gRPC and Service Mesh

## Overview
Build a production-ready microservices architecture using Go, gRPC, and Istio service mesh. Learn inter-service communication, observability, resilience patterns, and traffic management.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                      Kubernetes Cluster                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │  API     │  │ User     │  │ Order    │  │ Payment  │  │
│  │  Gateway │  │ Service  │  │ Service  │  │ Service  │  │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘  │
│       │             │             │             │         │
│       └─────────────┴─────────────┴─────────────┘         │
│                         │                                 │
│              ┌──────────▼──────────┐                       │
│              │    Istio Sidecar    │                       │
│              │  (envoy proxy xN)   │                       │
│              └─────────────────────┘                       │
│                         │                                 │
│        ┌────────────────┼────────────────┐                │
│        ▼                ▼                ▼                │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐            │
│  │ Postgres │    │  Redis   │    │  Kafka   │            │
│  │  (user)  │    │ (cache)  │    │ (events) │            │
│  └──────────┘    └──────────┘    └──────────┘            │
└─────────────────────────────────────────────────────────────┘
```

## Services
1. **API Gateway:** Entry point, authentication, rate limiting
2. **User Service:** CRUD operations, JWT tokens
3. **Order Service:** Order lifecycle management
4. **Payment Service:** Payment processing, fraud detection

## Tools
- Go (golang)
- gRPC + protobuf
- Istio / Linkerd
- Kubernetes
- Postgres, Redis, Kafka
- Jaeger (tracing)
- Prometheus + Grafana

## Learning Goals
- gRPC protocol design and implementation
- Service-to-service authentication (mTLS)
- Circuit breaker and retry patterns
- Distributed tracing
- Traffic splitting and canary deployments

## Build Milestones
- [ ] Week 1: Project setup and protobuf definitions
- [ ] Week 2: Implement User Service
- [ ] Week 3: Implement Order Service
- [ ] Week 4: Implement Payment Service
- [ ] Week 5: API Gateway with authentication
- [ ] Week 6: Deploy to Kubernetes with Istio
- [ ] Week 7: Add observability (tracing, metrics)
- [ ] Week 8: Implement resilience patterns
