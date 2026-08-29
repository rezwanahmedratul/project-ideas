# Container Image Security Scanner Pipeline

## Overview
An automated CI/CD pipeline that scans container images for vulnerabilities, secrets, misconfigurations, and base image freshness at every build stage — producing actionable reports and blocking deployments when critical issues are found.

## Architecture / Structure
- **Pipeline Stage 1**: Static analysis of Dockerfile for best practices
- **Pipeline Stage 2**: Image vulnerability scanning (CVE database lookup)
- **Pipeline Stage 3**: Secret detection (credentials, tokens, keys)
- **Pipeline Stage 4**: Compliance check against organizational policies
- **Pipeline Stage 5**: Report generation and Slack/email notifications

## Workflow
1. Triggered on push to registry or CI webhook
2. Pull new image and run multi-layer scan
3. Cross-reference CVEs with npm/pip/apt advisory databases
4. Flag exposed secrets using regex and entropy-based detection
5. Generate SARIF report for GitHub/ GitLab integration
6. Gate merge or deploy based on severity thresholds

## Tools
- Trivy or Grype for vulnerability scanning
- Gitleaks or truffleHog for secret detection
- Hadolint for Dockerfile linting
- Syft for SBOM generation
- GitHub Actions / GitLab CI for pipeline orchestration

## Learning Goals
- Container security fundamentals and supply chain attacks
- SBOM (Software Bill of Materials) standards
- Vulnerability database integration patterns
- CI/CD security gate implementation

## Build Milestones
1. Week 1: Dockerfile linting with hadolint + custom rules
2. Week 2: Trivy integration and CVE filtering by severity
3. Week 3: Secret detection with gitleaks + custom patterns
4. Week 4: SBOM generation and dependency tracking
5. Week 5: GitHub/GitLab PR comments and branch protection
6. Week 6: Dashboard with scan history and trend analysis
