# Terraform Plan Reviewer with Local LLM

**Category:** Combined  
**Date:** 2026-08-31

## Overview
A GitHub Action that reviews Terraform plans using a local LLM, checking for security issues, cost inefficiencies, and best practice violations before apply.

## Architecture
```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  Terraform Plan │────▶│  Local LLM      │────▶│  Review        │
│  (text output)  │     │  Analysis       │     │  Report        │
└─────────────────┘     └─────────────────┘     └────────┬────────┘
                                                        │
                                              ┌────────▼────────┐
                                              │  PR Comment /  │
                                              │  Status Check  │
                                              └─────────────────┘
```

## Workflow
1. Triggered on PR with Terraform changes
2. Run `terraform plan` and capture output
3. Send plan to local LLM (Ollama) for analysis
4. LLM checks for: security misconfigurations, cost issues, best practices
5. Post review as PR comment
6. Fail check if critical issues found

## Tools
- GitHub Actions
- Ollama (Llama 3, Qwen, or similar)
- Python for plan parsing
- Terraform CLI

## Learning Goals
- GitHub Actions development
- Terraform plan analysis
- Local LLM deployment and optimization
- Security policy enforcement

## Build Milestones
- [ ] Week 1: GitHub Action skeleton
- [ ] Week 2: Plan parsing and formatting
- [ ] Week 3: Ollama integration
- [ ] Week 4: Security rule checks
- [ ] Week 5: Cost estimation and warnings
- [ ] Week 6: PR comments and status checks
