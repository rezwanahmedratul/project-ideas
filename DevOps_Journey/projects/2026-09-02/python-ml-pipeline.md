# Project: Python ML Pipeline with Feature Store and Model Serving

## Overview
Build an end-to-end machine learning pipeline featuring automated feature engineering, model training, evaluation, and production serving with MLflow tracking and FastAPI endpoints.

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                 ML Pipeline Architecture                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐             │
│  │  Data    │───→│Features  │───→│  Train   │             │
│  │ Ingestion│    │  Store   │    │  Engine  │             │
│  └──────────┘    └──────────┘    └────┬─────┘             │
│       │                               │                   │
│       ▼                               ▼                   │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐             │
│  │  Pandas  │    │ Feast/   │    │  Scikit  │             │
│  │  Polars  │    │  Feature │    │  XGBoost │             │
│  │  DuckDB  │    │  Flag    │    │  Torch   │             │
│  └──────────┘    └──────────┘    └──────────┘             │
│                                                             │
│  ┌──────────────────────────────────────────────┐          │
│  │              MLflow Tracking                 │          │
│  │  - Experiment management                     │          │
│  │  - Model registry                            │          │
│  │  - Artifact storage                          │          │
│  └──────────────────────────────────────────────┘          │
│                      │                                      │
│                      ▼                                      │
│  ┌──────────────────────────────────────────────┐          │
│  │           FastAPI Model Serving              │          │
│  │  - REST endpoints                            │          │
│  │  - Batch inference                           │          │
│  │  - Auto-scaling                              │          │
│  └──────────────────────────────────────────────┘          │
└─────────────────────────────────────────────────────────────┘
```

## Components
1. **Data Pipeline:** Ingest, validate, transform raw data
2. **Feature Store:** Online/offline feature consistency
3. **Training Pipeline:** Automated retraining with validation
4. **Model Registry:** Version control and approval workflows
5. **Serving Layer:** Low-latency prediction API

## Tools
- Python 3.11+
- Polars (data manipulation)
- Feast (feature store)
- MLflow (experiment tracking)
- FastAPI (model serving)
- Scikit-learn / XGBoost
- Docker

## Learning Goals
- Feature engineering best practices
- MLOps pipeline design
- Model versioning and rollbacks
- Production serving patterns
- CI/CD for ML models

## Build Milestones
- [ ] Week 1: Data ingestion and cleaning
- [ ] Week 2: Feature store setup with Feast
- [ ] Week 3: Training pipeline with MLflow
- [ ] Week 4: Model evaluation and selection
- [ ] Week 5: Model registry configuration
- [ ] Week 6: FastAPI serving endpoint
- [ ] Week 7: Containerization and deployment
- [ ] Week 8: End-to-end testing and docs
