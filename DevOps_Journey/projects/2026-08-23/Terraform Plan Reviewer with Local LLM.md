# Terraform Plan Reviewer with Local LLM

**Category:** Combined (DevOps + AI)  
**Date:** 2026-08-23

---

## Overview

Create a tool that reviews Terraform plan outputs using a local LLM. Before applying infrastructure changes, the AI analyzes the planned modifications, flags potential risks (security misconfigurations, cost spikes, destructive changes), and suggests safer alternatives—all without sending plan data to external APIs.

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│         Terraform Plan Reviewer                      │
│                                                     │
│  ┌──────────┐    ┌──────────────┐    ┌───────────┐  │
│  │Terraform │───▶│  Plan       │───▶│  Parse &  │  │
│  │ Plan     │    │  Output     │    │  Extract  │  │
│  └──────────┘    └──────────────┘    └─────┬─────┘  │
│                                             │         │
│                                    ┌────────▼───────┐  │
│                                    │  Risk         │  │
│                                    │  Classification│  │
│                                    │  Engine       │  │
│                                    └───────┬───────┘  │
│                                            │           │
│                                    ┌───────▼───────┐  │
│                                    │  Local LLM    │  │
│                                    │  (Qwen 2.5)   │  │
│                                    └───────┬───────┘  │
│                                            │           │
│                                    ┌───────▼───────┐  │
│                                    │  Review       │  │
│                                    │  Report       │  │
│                                    │  (Markdown)   │  │
│                                    └──────────────┘  │
└─────────────────────────────────────────────────────┘
```

---

## Workflow

1. **Run** `terraform plan -out=plan.tfplan`
2. **Convert** plan to JSON: `terraform show -json plan.tfplan`
3. **Parse** changes: create/update/delete resources
4. **Flag** risky operations: public S3 buckets, opened security groups
5. **Score** risk level: low/medium/high/critical
6. **Generate** review report with suggestions
7. **Block** apply if critical issues found (optional)

---

## Tools & Stack

| Component | Technology |
|-----------|-----------|
| Terraform | HashiCorp Terraform |
| LLM | Ollama (Qwen 2.5, Llama 3.2) |
| Parser | Python + terraform-json |
| Scanner | Custom rules + linting |
| Integration | GitHub Action or pre-commit hook |
| Reporting | Markdown with color coding |

---

## Learning Goals

- Terraform plan interpretation
- Infrastructure risk assessment
- Local LLM integration in CI/CD
- Security scanning automation
- Structured output parsing
- Policy-as-code concepts

---

## Build Milestones

| Phase | Deliverable | Timeline |
|-------|-------------|----------|
| 1. Parser | Extract changes from terraform plan JSON | Week 1 |
| 2. Rules | Basic risk detection (public resources, no encryption) | Week 2 |
| 3. LLM Integration | Send plan summary to local LLM | Week 3 |
| 4. Prompt Design | Effective prompting for infrastructure review | Week 4 |
| 5. Report | Structured markdown output | Week 5 |
| 6. Blocker | Fail CI on critical findings | Week 6 |
| 7. Customization | Configurable risk thresholds | Week 7 |

---

## Reference Resources

- [Terraform Plan JSON Format](https://developer.hashicorp.com/terraform/cli/commands/plan#json-output)
- [terraform-json Python Package](https://pypi.org/project/terraform-json/)
- [Infracost for Cost Estimation](https://www.infracost.io/)
- [Checkov for Infrastructure Scanning](https://www.checkov.io/)
