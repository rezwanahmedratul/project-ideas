# Project: MLOps Model Registry & Experiment Tracking

## Overview
Implement a complete ML experiment tracking system with model registry, feature store integration, and automated model evaluation pipelines. Supports multiple frameworks (PyTorch, TensorFlow, scikit-learn).

## Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                    Experiment Pipeline                      │
├─────────────────┬─────────────────┬─────────────────────────┤
│  Feature Store  │  Training       │  Evaluation             │
│  (Feast/Tecton) │  (PyTorch/JAX)  │  (automated)            │
│                 │                 │                         │
│• Versioned      │• Hyperparameter │• Accuracy/F1/AUC        │
│  features       │  search         │• Drift detection        │
│• Point-in-time  │• Distributed    │• Bias analysis          │
│  consistency    │  training       │• Performance baseline   │
└────────┬────────┘                 └──────────┬──────────────┘
         │                                      │
         ▼                                      ▼
┌─────────────────┐                    ┌─────────────────┐
│  Metadata       │                    │  Model Registry │
│  Tracking       │                    │                 │
│  (MLflow/W&B)   │                    │• Version control│
│                 │                    │• Stage transitions│
│• Runs           │                    │• Artifact storage│
│• Parameters     │                    │• Promotion rules  │
│• Metrics        │                    │• Deployment ready │
│• Artifacts      │                    └────────┬────────┘
└─────────────────┘                             │
                                                ▼
                                         ┌─────────────────┐
                                         │  Inference      │
                                         │  Service        │
                                         │                 │
                                         │• A/B testing    │
                                         │• Canary deploy   │
                                         │• Auto-scaling    │
                                         └─────────────────┘
```

## Workflow
1. Data scientist logs experiments with parameters and metrics
2. Features versioned and retrieved from feature store
3. Training job completes → artifacts logged automatically
4. Best model registered in registry
5. Automated evaluation runs on validation set
6. Successful models promoted to staging production
7. Canary deployment with traffic splitting

## Tools & Tech Stack
- **MLflow** — Experiment tracking + model registry
- **Weights & Biases** — Alternative tracking platform
- **Feast** — Feature store (offline + online)
- **Kubeflow Pipelines** — Orchestration
- **Prometheus + Grafana** — Model monitoring
- **Evidently AI** — Drift detection
- **KServe** — Model serving on Kubernetes

## Learning Goals
- Experiment tracking best practices
- Feature store patterns (offline/online serving)
- Model versioning and lifecycle management
- Automated evaluation pipelines
- Production monitoring and drift detection
- MLOps CI/CD integration

## Build Milestones
1. [ ] Set up MLflow server with artifacts storage
2. [ ] Integrate Feast feature store
3. [ ] Build training pipeline with automatic logging
4. [ ] Configure model registry with stages
5. [ ] Add automated evaluation tests
6. [ ] Deploy model serving endpoint
7. [ ] Set up monitoring dashboards

## Reference Links
- [MLflow Documentation](https://mlflow.org/docs/latest/)
- [Feast Feature Store](https://feast.dev/)
- [Evidently AI](https://docs.evidentlyai.com/)
- [KServe Documentation](https://kserve.github.io/website/master/)
