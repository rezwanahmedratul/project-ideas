# AI/ML: Automated ML Experiment Tracker

## Overview
Create an experiment tracking system that automatically logs hyperparameters, metrics, datasets, and model artifacts for ML training runs — with AI-powered suggestions for next experiments based on past results.

## Architecture
```
Training Script → Experiment Logger
                              ├── Parameter Capture (auto-detect config)
                              ├── Metric Collector (wandb-like curves)
                              ├── Artifact Store (model checkpoints)
                              └── Suggestion Engine (Bayesian optimization)
         ↓
    Web Dashboard (Streamlit/Dash)
```

## Workflow
1. Wrap training script with experiment decorator
2. Automatically log hyperparameters, metrics, and artifact paths
3. Store runs in SQLite/PostgreSQL with MLflow-compatible API
4. Dashboard shows parameter sweeps, convergence plots, comparisons
5. AI suggests next hyperparameter combinations using Bayesian optimization

## Tools
Python, SQLite, MLflow (open-source), Optuna (Bayesian optimization), Streamlit

## Learning Goals
- MLOps experiment tracking principles
- Bayesian optimization for hyperparameter tuning
- MLflow API and deployment
- Visualization of high-dimensional parameter spaces

## Build Milestones
1. Build experiment logger that wraps training functions
2. Implement metric logging with real-time dashboard
3. Add artifact versioning for model checkpoints
4. Integrate Optuna for automated hyperparameter search
5. Build comparison view for side-by-side experiment analysis
