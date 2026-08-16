# Multi-Cloud Cost Anomaly Detector

## Overview
Build a system that monitors cloud spending across AWS, GCP, and Azure, detecting unusual cost spikes using statistical analysis and ML-based anomaly detection.

## Architecture
```
Cloud Billing APIs (AWS/GCP/Azure)
    ↓
Cost Data Aggregator
    ↓
Anomaly Detection Engine
    ↓
Alert System (Telegram/WhatsApp)
    ↓
Visualization Dashboard
```

## Workflow
1. Set up billing exports for each cloud provider
2. Create unified data schema for cost metrics
3. Implement baseline cost modeling (daily/weekly patterns)
4. Build anomaly detection with z-score or Isolation Forest
5. Add threshold-based and ML-based alerts
6. Create dashboard showing spend trends

## Tools
- Python (pandas, scikit-learn)
- AWS Cost Explorer API
- GCP Billing API
- Azure Cost Management API
- PostgreSQL for storage
- Grafana for visualization

## Learning Goals
- Cloud cost optimization strategies
- Time series anomaly detection
- Multi-cloud billing normalization
- Financial operations (FinOps) principles

## Build Milestones
- [ ] Fetch billing data from all 3 providers
- [ ] Build unified cost database schema
- [ ] Implement baseline daily cost model
- [ ] Add z-score anomaly detection
- [ ] Set up Telegram alerts
- [ ] Create Grafana dashboard

## References
- https://docs.aws.amazon.com/costexplorer/
- https://cloud.google.com/billing
- https://azure.microsoft.com/en-us/products/cost-management/
