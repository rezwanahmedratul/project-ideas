# Terraform Sentinel Security Policy Enforcement
**Date:** 2026-09-03  
**Category:** Combined  
**Complexity:** Intermediate

---

## Overview

Implement a comprehensive security policy enforcement system using Terraform Sentinel that automatically validates infrastructure changes against organizational security standards before deployment.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│         Terraform Sentinel Security Enforcement             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Terraform Plan ─────────────────────────────────▶          │
│                           │                                 │
│                    ┌──────▼───────────┐                    │
│                    │   Sentinel       │                    │
│                    │   Policy Engine  │                    │
│                    └──────┬───────────┘                    │
│                           │                                 │
│         ┌─────────────────┼─────────────────┐               │
│         │                 │                 │               │
│    ┌────▼────┐      ┌────▼────┐      ┌────▼────┐          │
│    │Rule 1:  │      │Rule 2:  │      │Rule 3:  │          │
│    │Storage  │      │Compute  │      │Network  │          │
│    │Security│      │Hardening│      │Policies │          │
│    └────┬────┘      └────┬────┘      └────┬────┘          │
│         │                │                │                │
│    ┌────▼────┐      ┌────▼────┐      ┌────▼────┐          │
│    │S3      │      │EC2     │      │SG     │          │
│    │Encryption│     │IMDSv2 │      │Rules │          │
│    │Enabled  │      │Require│      │Open │          │
│    └─────────┘      └────────┘      └──────┘           │
│                           │                                 │
│                    ┌──────▼───────────┐                    │
│                    │   Compliance     │                    │
│                    │   Report         │                    │
│                    └──────┬───────────┘                    │
│                           │                                │
│                    ┌──────▼───────────┐                    │
│                    │   Pass/Fail      │                    │
│                    └──────────────────┘                    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## Policy Rules

### Storage Security Policies
```sentinel
rule "s3_encryption_required" {
    main resource with aws_s3_bucket as r {
        if !r.server_side_encryption_configuration {
            return false
        }
        for r.server_side_encryption_configuration.rule as rule {
            if !rule.apply_server_side_encryption_by_default {
                return false
            }
        }
    }
    pass
}

rule "s3_versioning_enabled" {
    main resource with aws_s3_bucket as r {
        if !r.versioning || !r.versioning.enabled {
            return false
        }
    }
    pass
}
```

### Compute Security Policies
```sentinel
rule "ec2_imdsv2_required" {
    main resource with aws_instance as r {
        if r.metadata_options {
            if r.metadata_options.http_tokens != "required" {
                return false
            }
        } else {
            return false
        }
    }
    pass
}

rule "no_public_ssh" {
    main resource with aws_security_group_rule as r {
        if r.type == "ingress" && r.cidr_blocks.contains("0.0.0.0/0") {
            if r.from_port == 22 {
                return false
            }
        }
    }
    pass
}
```

### Network Security Policies
```sentinel
rule "vpc_flow_logs_enabled" {
    main resource with aws_flow_log as r {
        return true
    }
    pass
}

rule "no_open_internet_gateway" {
    main resource with aws_internet_gateway as ig {
        for ig in ig as gateway {
            if gateway.attachment {
                return false
            }
        }
    }
    warn
}
```

## Compliance Reporting

```yaml
policy_check:
  timestamp: "2026-09-03T10:00:00Z"
  plan_id: "abc-123-def"
  results:
    passed:
      - rule: s3_encryption_required
        resources: [aws_s3_bucket.main, aws_s3_bucket.logs]
      - rule: ec2_imdsv2_required
        resources: [aws_instance.web]
    failed:
      - rule: no_open_ssh
        resources: 
          - aws_security_group_rule.ssh_open
        suggestion: "Restrict SSH to VPN CIDR range"
    warnings:
      - rule: vpc_flow_logs_enabled
        resources: []
        suggestion: "Enable flow logs for better monitoring"
  compliance_score: 85
  action: "block"  # or "warn" or "allow"
```

## Integration Patterns

### CI/CD Integration
```bash
# In GitHub Actions pipeline
- name: Run Sentinel policies
  run: |
    terraform plan -out=tfplan
    sentinel validate -config=sentinel.hcl tfplan
    
# In GitLab CI
stages:
  - validate
  - plan
  - apply

validate:
  script:
    - terraform-fmt-check
    - checkov -d .
    - sentinel-check
```

### Pull Request Notifications
- Comment on PR with policy results
- Block merge if critical policies fail
- Allow override with approval workflow

## Tools & Technologies

- **Terraform Enterprise** or **OpenTofu**
- **Sentinel** policy language
- **Python** for custom policy logic
- **GitHub Actions** / **GitLab CI** for automation
- **Slack** for notifications

## Learning Goals

- Master Sentinel policy language
- Understand infrastructure compliance automation
- Implement security-as-code practices
- Design policy enforcement workflows
- Integrate security into CI/CD pipelines

## Build Milestones

| Milestone | Description |
|-----------|-------------|
| M1 | Set up Sentinel with OpenTofu |
| M2 | Write storage security policies |
| M3 | Implement compute hardening policies |
| M4 | Add network security rules |
| M5 | Create compliance reporting dashboard |
| M6 | Integrate with CI/CD and add PR notifications |

## Reference Links

- [Sentinel Documentation](https://developer.hashicorp.com/sentinel/docs)
- [OpenTofu Sentinel](https://opentofu.org/docs/enterprise/sentinel/)
- [Security Best Practices for Terraform](https://www.terraform.io/cloud-docs/sentinel)
- [Checkov for static analysis](https://www.checkov.io/)
