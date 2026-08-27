# Terraform Plan Reviewer with Local LLM

**Date:** 2026-08-27
**Category:** Combined (DevOps + AI)
**Tags:** terraform, llm, code-review, security, local-ai

---

## Overview

A pre-commit hook or CI check that reviews Terraform plans using a local LLM. It analyzes proposed infrastructure changes for security risks, cost implications, best practice violations, and suggests improvements — all running offline.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│              Pre-Commit / CI Hook                           │
│                                                             │
│  terraform plan ──▶ JSON output                             │
│        │                                                    │
│        ▼                                                    │
│  ┌─────────────────────────────────────┐                    │
│  │     Terraform Plan Reviewer         │                    │
│  │                                     │                    │
│  │  ┌─────────────┐  ┌──────────────┐  │                    │
│  │  │ Plan Parser │  │ LLM Reviewer │  │                    │
│  │  │ (JSON→Text) │─▶│ (Ollama/Qwen)│  │                    │
│  │  └─────────────┘  └──────┬───────┘  │                    │
│  │                          │          │                    │
│  │              ┌───────────▼───────┐   │                    │
│  │              │  Policy Engine    │   │                    │
│  │              │  (Custom rules)   │   │                    │
│  │              └───────────┬───────┘   │                    │
│  │                          │           │                    │
│  │              ┌───────────▼───────┐   │                    │
│  │              │  Report Generator │   │                    │
│  │              └───────────────────┘   │                    │
│  └─────────────────────────────────────┘                    │
│                          │                                  │
│                          ▼                                  │
│              Review comment / exit code                     │
└─────────────────────────────────────────────────────────────┘
```

## Review Categories

### Security Checks
- Publicly accessible resources (S3 buckets, security groups)
- Hardcoded credentials or secrets
- Missing encryption at rest
- Overly permissive IAM policies
- Unencrypted databases

### Cost Checks
- Expensive instance types for dev/workload
- Unused resource recommendations
- Reserved instance opportunities
- Data transfer cost warnings

### Best Practice Checks
- Missing tags for cost allocation
- No lifecycle rules on storage
- Single-AZ deployments for production
- Missing backup configuration
- No monitoring/alerting

### Drift Prevention
- Resources that should be managed but aren't
- Manual changes that will be overwritten
- State file synchronization issues

## LLM Integration

### Local Model Options
- **Qwen2.5-7B-Instruct** — excellent instruction following
- **Phi-3.5-mini** — fast, good for simple reviews
- **DeepSeek-Coder-V2-Lite** — strong at infrastructure-as-code

### Prompt Template
```
You are a senior DevOps engineer reviewing a Terraform plan.
Analyze the following plan for security risks, cost concerns,
and best practice violations.

Plan summary:
{plan_summary}

Resources to create: {create_count}
Resources to update: {update_count}
Resources to destroy: {destroy_count}

Provide:
1. Security risks (critical/high/medium/low)
2. Cost optimization suggestions
3. Best practice violations
4. Overall risk assessment
```

## Implementation Approaches

### Approach A: Pre-commit Hook
- Runs `terraform plan` locally
- Reviews output before commit
- Fast feedback loop
- Blocks unsafe changes

### Approach B: CI Check
- Runs in GitHub Actions
- Reviews merged plan from PR
- Comments on pull request
- Can enforce pass/fail thresholds

### Approach C: Standalone CLI
- Accepts plan JSON as input
- Can be integrated into any workflow
- Batch review mode for multiple plans

## Tools

- **Python 3.11+** or **Go**
- **Ollama** or **llama.cpp** server
- **Pydantic** for plan schema parsing
- **Click** for CLI interface
- **pytest** for testing review rules

## Learning Goals

- Terraform plan format deep dive
- Infrastructure security scanning patterns
- Local LLM integration and prompt design
- Policy-as-code implementation
- Pre-commit hook development

## Build Milestones

1. [ ] Parse Terraform plan JSON into structured format
2. [ ] Implement rule-based security checks (no LLM needed)
3. [ ] Add cost estimation and optimization suggestions
4. [ ] Integrate local LLM for natural language review
5. [ ] Build pre-commit hook wrapper
6. [ ] Add CI integration (GitHub Actions)
7. [ ] Implement configurable policy thresholds
8. [ ] Create example ruleset and documentation

---
*Generated: 2026-08-27*
