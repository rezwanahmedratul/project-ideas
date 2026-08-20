# GitOps Secret Rotator

**Category:** DevOps  
**Date:** 2026-08-19  
**Difficulty:** Intermediate  

## Overview
A controller that automates **periodic rotation of secrets** in a GitOps-managed cluster without committing plaintext to Git. It integrates with an external secrets manager (Vault, SOPS, or sealed-secrets) and reconciles rotated values into Kubernetes `Secret` objects on a schedule, keeping Git as the source of truth for *references* while secrets live encrypted or in a manager.

## Architecture / Structure
```
secret-rotator/
├── controller/          # Rotation loop (Python/Go)
├── providers/           # Vault, AWS Secrets Manager, SOPS backends
├── manifests/           # SealedSecret / ExternalSecret templates
├── policies/            # Rotation schedules per secret class
├── tests/               # Unit + integration tests
└── README.md
```

## Workflow
1. Cluster uses External Secrets Operator or sealed-secrets to sync from a manager.
2. The rotator reads a `RotationPolicy` (e.g., every 30 days for DB creds).
3. On schedule, it mutes alerts, generates new value in the manager, updates the reference, and forces a re-sync.
4. Applications pick up the new secret via rolling restart or dynamic reload.
5. Old value is retired after a grace period.

## Tools
- Kubernetes, External Secrets Operator or sealed-secrets
- HashiCorp Vault or cloud KMS / SOPS
- Python (or Go) for the controller
- CronJob / kubernetes operator pattern
- Prometheus alert silencing (Alertmanager)

## Learning Goals
- Secure secret management in GitOps workflows.
- Build a reconciliation loop (observe → diff → act).
- Integrate with a KMS / Vault.
- Zero-downtime credential rotation.

## Build Milestones
1. Set up SOPS + age encryption for a test secret in Git.
2. Write a script that rotates a value in the manager and re-syncs.
3. Add a `RotationPolicy` CRD/config and scheduling logic.
4. Wire graceful app reload (signal or rolling restart).
5. Add metrics (last-rotated age) + a "rotation due" alert.
