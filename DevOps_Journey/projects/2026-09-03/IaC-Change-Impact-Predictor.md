# IaC Change Impact Predictor
**Date:** 2026-09-03  
**Category:** Combined  
**Complexity:** Intermediate

---

## Overview

Build a tool that analyzes Infrastructure as Code (Terraform/Pulumi) changes and predicts their impact on the existing environment, helping teams understand risks before applying changes.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│              IaC Change Impact Predictor                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Input: Terraform Plan / Pulumi Preview                     │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ terraform plan -out=plan.tfplan                      │   │
│  └─────────────────────────────────────────────────────┘   │
│                           │                                 │
│                    ┌──────▼───────────┐                    │
│                    │   Plan Parser    │                    │
│                    │   • Resource add │                    │
│                    │   • Resource del │                    │
│                    │   • Resource mod │                    │
│                    └──────┬───────────┘                    │
│                           │                                │
│                    ┌──────▼───────────┐                    │
│                    │   Dependency     │                    │
│                    │   Graph Builder  │                    │
│                    │   • Resource map │                    │
│                    │   • Link analysis│                    │
│                    └──────┬───────────┘                    │
│                           │                                │
│                    ┌──────▼───────────┐                    │
│                    │   Impact Analyzer│                    │
│                    │   • Breaking     │                    │
│                    │     changes      │                    │
│                    │   • Side effects │                    │
│                    │   • Downtime     │                    │
│                    │     estimation   │                    │
│                    └──────┬───────────┘                    │
│                           │                                │
│                    ┌──────▼───────────┐                    │
│                    │   Risk Scoring   │                    │
│                    │   • Severity     │                    │
│                    │   • Confidence   │                    │
│                    │   • Mitigation   │                    │
│                    └──────┬───────────┘                    │
│                           │                                │
│                    ┌──────▼───────────┐                    │
│                    │   Report         │                    │
│                    │   • Summary      │                    │
│                    │   • Warnings     │                    │
│                    │   • Recommendations│                  │
│                    └──────────────────┘                    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## Impact Categories

### High Risk (Red)
| Change Type | Example | Impact |
|-------------|---------|--------|
| Database schema change | ALTER TABLE DROP COLUMN | Data loss risk |
| Security group reduction | Remove ingress rule | Access denied |
| Instance type downgrade | t3.medium → t2.micro | Performance drop |
| AZ migration | Change availability zone | Downtime expected |

### Medium Risk (Yellow)
| Change Type | Example | Impact |
|-------------|---------|--------|
| Auto-scaling adjustment | Min: 2 → Max: 4 | Capacity change |
| Storage expansion | Volume resize | No downtime usually |
| Certificate renewal | SSL cert update | Brief interruption |
| Configuration change | App setting update | Restart needed |

### Low Risk (Green)
| Change Type | Example | Impact |
|-------------|---------|--------|
| New resource addition | Add S3 bucket | No existing impact |
| Tag modification | Add description tag | Cosmetic only |
| Logging enablement | Turn on audit logs | Performance slight impact |

## Dependency Graph Analysis

```python
dependency_map = {
    "aws_instance.web": ["aws_security_group.web"],
    "aws_db_instance.main": ["aws_db_subnet_group.main", "aws_security_group.db"],
    "aws_alb.main": ["aws_lb_listener.https", "aws_lb_target_group.main"],
}

def analyze_dependencies(resource_changes, dependency_map):
    affected_resources = set()
    for change in resource_changes:
        if change.address in dependency_map:
            affected_resources.update(dependency_map[change.address])
    return affected_resources
```

## Output Format

```yaml
summary:
  total_changes: 12
  high_risk: 2
  medium_risk: 3
  low_risk: 7
  estimated_downtime: "5 minutes"
  cost_change: "+$45/month"

warnings:
  - level: high
    resource: aws_db_instance.main
    message: "Database instance type change will cause replacement"
    recommendation: "Create snapshot before change"

risk_scores:
  aws_instance.web: 0.7
  aws_security_group.web: 0.3
```

## Tools & Technologies

- **Python** with `tfplan` parser library
- **NetworkX** for dependency graph analysis
- **Terrascan** for policy checks
- **Checkov** for security scanning
- **Typoscanner** for drift detection
- **GitHub Actions** integration

## Learning Goals

- Understand Terraform state and resource dependencies
- Learn infrastructure change impact analysis
- Implement graph traversal for dependency mapping
- Build security-aware IaC analysis tools
- Create actionable reporting systems

## Build Milestones

| Milestone | Description |
|-----------|-------------|
| M1 | Parse Terraform plan output |
| M2 | Extract resource changes and attributes |
| M3 | Build dependency graph from provider metadata |
| M4 | Implement risk scoring algorithm |
| M5 | Add security policy checking |
| M6 | Generate human-readable reports |

## Reference Links

- [Terraform Plan Format](https://developer.hashicorp.com/terraform/language/resources/dependencies)
- [Terrascan Security Policies](https://terrascan.io/)
- [Checkov Infrastructure Scanning](https://www.checkov.io/)
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
