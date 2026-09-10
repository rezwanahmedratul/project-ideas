# Project Idea: Terraform Cost Optimizer

## Overview
Automated cost analysis and optimization recommendations for Terraform-managed infrastructure across AWS, Azure, and GCP.

## Architecture
- CLI tool written in Go
- Terraform state parsing
- Cloud provider cost APIs integration
- Report generation (CLI + web dashboard)

## Workflow
1. Scan Terraform configurations
2. Query cloud provider pricing APIs
3. Identify over-provisioned resources
4. Generate optimization report with estimated savings

## Tools
- Go, Terraform CLI
- AWS Cost Explorer API
- Azure Cost Management API
- Google Cloud Billing API

## Learning Goals
- Infrastructure-as-Code cost modeling
- Cloud pricing structures across providers
- Multi-cloud cost comparison
- Automated reporting pipelines

## Build Milestones
1. AWS-only single-account support
2. Add Azure and GCP
3. Historical cost trending
4. Auto-remediation suggestions
