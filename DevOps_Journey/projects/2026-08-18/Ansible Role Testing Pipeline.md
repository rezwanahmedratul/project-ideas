# Ansible Role Testing Pipeline

**Category:** DevOps  
**Date:** 2026-08-18  
**Difficulty:** Beginner-Intermediate

---

## Overview

A CI/CD pipeline that automatically tests Ansible roles across multiple OS versions using molecule + docker, with linting, idempotency checks, and coverage reporting. Perfect for homelab users managing NixOS, Debian, and Ubuntu nodes with Ansible.

## Architecture / Structure

```
ansible-test-pipeline/
├── .github/workflows/
│   └── test.yml           # Matrix: debian12, ubuntu24, nixos
├── molecule/
│   ├── default/
│   │   ├── molecule.yml   # Docker driver config
│   │   ├── converge.yml   # Apply role
│   │   └── verify.yml     # Assertions
│   └── shared/
│       └── playbook.yml
├── roles/
│   └── <your-role>/
│       ├── tasks/main.yml
│       ├── defaults/main.yml
│       └── meta/main.yml
├── tests/
│   └── idempotency.sh     # Run twice, diff output
└── Makefile               # Local dev shortcuts
```

## Workflow

1. **Lint:** `ansible-lint` + `yamllint` on every PR
2. **Molecule converge:** Spin up Docker container, apply role
3. **Idempotency:** Re-run, assert no changes (ansible-playbook --check)
4. **Verify:** Run InSpec/Testinfra assertions
5. **Matrix:** Repeat across Debian 12, Ubuntu 24.04, (NixOS via VM)
6. **Report:** Upload coverage + lint results as PR comments

## Tools

- **Provisioning:** Ansible 10.x, ansible-lint
- **Testing:** Molecule, Docker, Testinfra/InSpec
- **CI:** GitHub Actions, GitLab CI
- **Reporting:** JUnit XML, coverage badges

## Learning Goals

- Write idempotent, lint-clean Ansible roles
- Use Molecule scenarios for multi-OS testing
- Implement CI matrix workflows
- Understand infrastructure testing pyramid

## Build Milestones

| Milestone | Deliverable | Est. Time |
|-----------|-------------|-----------|
| M1 | One Ansible role + ansible-lint clean | 1 day |
| M2 | Molecule default scenario (Docker) | 1 day |
| M3 | Idempotency + verify tests | 1 day |
| M4 | GitHub Actions matrix CI | 1 day |
| M5 | Coverage reporting + badges | 0.5 day |

---

**Tags:** #ansible #ci-cd #molecule #testing #infrastructure-as-code
