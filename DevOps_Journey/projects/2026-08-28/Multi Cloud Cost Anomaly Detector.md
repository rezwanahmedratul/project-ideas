# DevOps: Multi-Cloud Cost Anomaly Detector

## Overview
Build a service that aggregates billing data from AWS, GCP, and Azure, uses statistical anomaly detection to identify unexpected cost spikes, and notifies teams with actionable context about which services or regions are driving the deviation.

## Architecture
```
Cloud Billing APIs → Cost Aggregator (Python)
                           ├── Anomaly Engine (Isolation Forest / Prophet)
                           ├── Attribution Service (tag/resource mapping)
                           └── Alert Dispatcher (Slack/Email/PagerDuty)
```

## Workflow
1. Daily sync of billing data from all three clouds
2. Compute baseline spend per service/region/team
3. Detect deviations beyond configurable thresholds
4. Attribute anomaly to specific resources using tag hierarchy
5. Push alert with "top 3 cost drivers" and recommended actions

## Tools
AWS Cost Explorer API, GCP Billing API, Azure Cost Management API, Python, Prophet, Redis

## Learning Goals
- Multi-cloud billing reconciliation
- Time-series anomaly detection
- Tag-based cost attribution
- Cloud FinOps practices

## Build Milestones
1. Build unified billing data model across providers
2. Implement baseline calculation and anomaly detection
3. Add resource attribution via cloud tagging
4. Create dashboard with trend visualization
5. Integrate with alerting channels (Slack, webhook)
