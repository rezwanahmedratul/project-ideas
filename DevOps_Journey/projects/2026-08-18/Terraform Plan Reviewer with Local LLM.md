# Terraform Plan Reviewer with Local LLM

**Category:** Combined  
**Date:** 2026-08-18  
**Difficulty:** Intermediate

---

## Overview

A pre-merge GitOps check that runs `terraform plan`, parses the diff, and uses a local LLM to flag risky changes (destroyed resources, open security groups, cost spikes) with human-readable explanations. Integrates as a GitHub Action / CI step for your Proxmox + AWS homelab IaC.

## Architecture / Structure

```
tf-reviewer/
├── cmd/
│   └── review.go         # CLI: tf plan → review
├── internal/
│   ├── parse/            # HCL plan JSON parser
│   ├── rules/            # Static risk heuristics
│   ├── llm/              # Ollama client
│   └── report/           # Markdown/PR comment builder
├── examples/
│   └── github-action.yml
└── config.yaml           # Model, risk thresholds
```

## Workflow

1. CI runs `terraform plan -out=tfplan` → `show -json`
2. **Parse** extracts create/update/delete/destroy actions
3. **Rules** flag: `destroy` on stateful resources, `0.0.0.0/0` ingress, IAM `*` 
4. **LLM** summarizes changes in natural language + risk rating
5. **Report** posted as PR comment with approve/request-changes suggestion
6. Blocks merge if critical risk + no human override

## Tools

- **IaC:** Terraform, OpenTofu, HCL
- **LLM:** Ollama (codellama:13b, qwen2.5-coder:7b)
- **CI:** GitHub Actions, GitLab CI
- **Language:** Go or Python
- **Parse:** terraform show JSON output

## Learning Goals

- Terraform plan JSON structure
- Static analysis of IaC for security/cost
- LLM summarization of structured diffs
- CI gates and policy-as-code patterns

## Build Milestones

| Milestone | Deliverable | Est. Time |
|-----------|-------------|-----------|
| M1 | Parse terraform plan JSON | 1 day |
| M2 | Static risk rules (destroy, SG, IAM) | 1 day |
| M3 | LLM natural-language summary | 1 day |
| M4 | PR comment reporter | 1 day |
| M5 | GitHub Action wrapper | 0.5 day |

---

**Tags:** #terraform #iac #llm #ci-cd #security #devops #local-ai
