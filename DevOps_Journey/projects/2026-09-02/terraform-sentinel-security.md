# Project: Secure Cloud Infrastructure with Terraform and Sentinel

## Overview
Create a production-ready infrastructure framework enforcing security policies at deployment time using HashiCorp Sentinel. Prevent misconfigurations before they reach production.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│           Policy-as-Code Enforcement                        │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌─────────────────────────────────────────────────────┐   │
│  │              Terraform Plan                         │   │
│  │         (Resource Configuration)                    │   │
│  └────────────────────────┬────────────────────────────┘   │
│                           │                                 │
│                           ▼                                 │
│  ┌─────────────────────────────────────────────────────┐   │
│  │           Sentinel Policy Engine                    │   │
│  │                                                     │   │
│  │  ┌─────────────────────────────────────────────┐   │   │
│  │  │  Prevent Rules (must pass)                  │   │   │
│  │  │  - No public S3 buckets                     │   │   │
│  │  │  - Encryption required on storage           │   │   │
│  │  │  - No SSH from internet                     │   │   │
│  │  │  - Required tags present                    │   │   │
│  │  └─────────────────────────────────────────────┘   │   │
│  │                                                     │   │
│  │  ┌─────────────────────────────────────────────┐   │   │
│  │  │  Inform Rules (warnings only)              │   │   │
│  │  │  - Cost optimization suggestions            │   │   │
│  │  │  - Region best practices                    │   │   │
│  │  │  - Resource naming conventions              │   │   │
│  │  └─────────────────────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────┘   │
│                           │                                 │
│              ┌────────────┼────────────┐                   │
│              ▼            ▼            ▼                    │
│        ┌──────────┐  ┌──────────┐  ┌──────────┐          │
│        │  ALLOW   │  │ WARN     │  │  DENY    │          │
│        │  Deploy  │  │ Review   │  │  Block   │          │
│        │          │  │ Required │  │          │          │
│        └──────────┘  └──────────┘  └──────────┘          │
└─────────────────────────────────────────────────────────────┘
```

## Policy Categories
1. **Security:** Encryption, access control, network isolation
2. **Compliance:** Tagging, budget controls, region restrictions
3. **Cost:** Instance right-sizing, reserved instance recommendations
4. **Operational:** High availability, backup requirements

## Tools
- Terraform
- HashiCorp Sentinel
- tfsec (complementary scanning)
- Checkov (alternative policy engine)
- GitHub Actions (CI integration)

## Learning Goals
- Policy-as-code principles
- Sentinel language fundamentals
- Prevent vs. inform policy design
- CI/CD policy enforcement
- Cost governance automation

## Build Milestones
- [ ] Week 1: Terraform state and Sentinel setup
- [ ] Week 2: Security prevent policies
- [ ] Week 3: Compliance inform policies
- [ ] Week 4: Cost governance rules
- [ ] Week 5: GitHub Actions integration
- [ ] Week 6: Policy testing and debugging
- [ ] Week 7: Multi-cloud policy application
- [ ] Week 8: Dashboard and reporting
