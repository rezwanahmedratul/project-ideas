# Terraform Plan Reviewer with Local LLM

## Overview
A GitHub Action that runs terraform plan and sends the output to a local LLM for security review, cost analysis, and plain-language explanation. Catches misconfigurations before they reach production.

## Architecture / Structure
- **GitHub Action**: Triggered on PR with Terraform changes
- **Plan Extractor**: Parses terraform plan JSON output
- **LLM Reviewer**: Sends structured diffs to local Ollama endpoint
- **Policy Checker**: Validates against OPA/Conftest rules
- **Comment Generator**: Posts reviewed findings as PR comments
- **Summary Report**: Creates markdown report with risk scores

## Review Categories
1. **Security**: Open ports, unencrypted storage, missing IAM policies
2. **Cost**: Unexpected instance types, orphaned resources, region selection
3. **Best Practices**: Naming conventions, tag compliance, module usage
4. **Drift Detection**: Comparison with known-good state
5. **Impact Assessment**: What changes affect which services

## Workflow
1. Developer opens PR modifying Terraform config
2. GitHub Action runs terraform plan on diff branch
3. Plan JSON sent to local LLM with review prompt
4. LLM returns categorized findings with explanations
5. Policy check runs Conftest rules against plan
6. Comments posted to PR with risk indicators
7. Fails check if critical security issues found

## Tools
- GitHub Actions (action.yml)
- terraform (official binary)
- Ollama for local LLM inference
- Conftest for policy validation
- Python for plan parsing and comment generation

## Learning Goals
- Terraform plan format and diff analysis
- GitHub Actions for CI/CD
- Infrastructure security best practices
- OPA/Rego policy writing
- LLM prompt engineering for code review

## Build Milestones
1. Week 1: GitHub Action skeleton with terraform plan
2. Week 2: Plan JSON parsing and field extraction
3. Week 3: Ollama integration with structured prompts
4. Week 4: Security rule definitions and Conftest policies
5. Week 5: PR comment posting with formatting
6. Week 6: Summary report generation and dashboard
