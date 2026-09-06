# Infrastructure Change Impact Predictor using ML

## Overview
Build a machine learning system that predicts the blast radius of infrastructure changes before they're applied, helping teams understand the impact of Terraform plans.

## Architecture
```
┌─────────────────────────────────────────┐
│   Change Impact Predictor               │
├─────────────────────────────────────────┤
│  Input Features                         │
│  ├─ Terraform plan diff                 │
│  ├─ Dependency graph                    │
│  ├─ Historical incident data            │
│  └─ Service criticality scores          │
├─────────────────────────────────────────┤
│  ML Model                               │
│  ├─ Graph neural network                │
│  ├─ Feature importance analysis         │
│  └─ Uncertainty quantification          │
├─────────────────────────────────────────┤
│  Output                                 │
│  ├─ Risk score (0-100)                  │
│  ├─ Affected services list              │
│  └─ Confidence interval                 │
└─────────────────────────────────────────┘
```

## Workflow
1. Capture Terraform plan before apply
2. Extract change features
3. Run through impact prediction model
4. Return risk assessment and affected services
5. Recommend review level based on risk score

## Tools
- Python (PyTorch Geometric)
- Terraform CLI
- Service dependency graph
- Historical incident database

## Learning Goals
- Graph neural networks
- Change risk assessment
- ML interpretability
- Infrastructure correlation

## Build Milestones
- [ ] Week 1: Feature extraction from plans
- [ ] Week 2: Dependency graph construction
- [ ] Week 3: Model training
- [ ] Week 4: Prediction API
- [ ] Week 5: Integration with CI/CD
- [ ] Week 6: Accuracy validation
