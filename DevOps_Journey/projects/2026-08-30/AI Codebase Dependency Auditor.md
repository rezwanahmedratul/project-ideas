# AI Codebase Dependency Auditor

## Overview
An automated tool that audits project dependencies for security vulnerabilities, license compliance, and upgrade recommendations. Uses AI to prioritize fixes based on exploitability and project impact.

## Architecture / Structure
- **Dependency Scanner**: Parses package manifests (package.json, requirements.txt, go.mod, Cargo.toml)
- **Vulnerability DB**: Queries CVE databases (NVD, GitHub Advisories, OSV)
- **License Checker**: Identifies license compatibility issues
- **AI Prioritizer**: Ranks findings by exploit likelihood and business impact
- **Fix Proposer**: Suggests upgrade paths or workarounds
- **Report Generator**: HTML/PDF reports with actionable items

## Workflow
1. Scan project for all dependency layers (direct + transitive)
2. Query vulnerability databases for known CVEs
3. Check licenses for compatibility with project license
4. AI analyzes: Is this CVE actively exploited? Does my project use the vulnerable code path?
5. Generate prioritized fix list with upgrade commands
6. Create dependency lock files with vetted versions
7. Schedule regular re-scans and notify on new vulnerabilities

## Tools
- npm audit / pip-audit / cargo audit for base scanning
- GitHub Advisory Database API
- SPDX license list for compliance checking
- Ollama for AI prioritization prompts
- Python for orchestration and reporting
- GitHub Actions integration for CI scanning

## Learning Goals
- Supply chain security fundamentals
- CVE analysis and exploitability assessment
- License compliance in open source projects
- Dependency management at scale
- Security automation in CI/CD pipelines

## Build Milestones
1. Week 1: Multi-language dependency scanner skeleton
2. Week 2: Vulnerability database integration
3. Week 3: License checking and compliance matrix
4. Week 4: AI-powered risk prioritization logic
5. Week 5: Fix proposal generator with upgrade commands
6. Week 6: Reporting dashboard and CI/CD integration
