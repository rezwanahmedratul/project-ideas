# Project: Kubernetes Operator for Custom Resource

## Overview
Build a Kubernetes operator that manages a custom resource type. Implements the controller pattern, watches for resource changes, and reconciles cluster state to desired state automatically.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                     Kubernetes Cluster                      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐     │
│  │   User      │    │  Controller │    │   CRD       │     │
│  │  applies    │───▶│  reconciles │◄───│  defines    │     │
│  │  YAML/      │    │  spec→status│    │  schema     │     │
│  │  kubectl    │    │             │    │             │     │
│  └─────────────┘    └──────┬──────┘    └─────────────┘     │
│                            │                                │
│                   ┌────────▼────────┐                       │
│                   │   Custom        │                       │
│                   │   Resource      │                       │
│                   │  (Managed Pods, │                       │
│                   │   Services, etc)│                       │
│                   └─────────────────┘                       │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Operator Binary                                     │   │
│  │  • Watch API server                                  │   │
│  │  • Reconcile loops                                   │   │
│  │  • Handle events                                     │   │
│  └──────────────────────────────────────────────────────┘   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## Workflow
1. Define Custom Resource Definition (CRD) with API schema
2. Implement operator controller using kubebuilder
3. Watch for Create/Update/Delete events
4. Reconcile function ensures actual state matches desired state
5. Operator scales resources, creates services, manages rollouts

## Example Use Case
Build an operator for "ScheduledBackup" resource that manages database backups on a schedule, handling failures and notifications.

## Tools & Tech Stack
- **Kubebuilder** — Operator scaffolding framework
- **controller-runtime** — Go library for operators
- **client-go** — Kubernetes client library
- **make** — Build automation
- **kind** — Local Kubernetes testing
- **Helm** — Operator packaging for distribution

## Learning Goals
- Kubernetes API and custom resources
- Operator pattern and reconciliation loop
- Go programming for cloud-native
- CRD design and OpenAPI validation
- Unit and integration testing for operators
- Operator lifecycle management

## Build Milestones
1. [ ] Install kubebuilder and initialize project
2. [ ] Create CRD with API specification
3. [ ] Implement reconcile loop for basic operations
4. [ ] Add status subresource updates
5. [ ] Write unit tests with envtest
6. [ ] Deploy operator on kind cluster
7. [ ] Package as Helm chart and publish

## Reference Links
- [Kubebuilder Documentation](https://kubebuilder.io/)
- [Kubernetes Operators Pattern](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/)
- [controller-runtime Guide](https://pkg.go.dev/sigs.k8s.io/controller-runtime)
