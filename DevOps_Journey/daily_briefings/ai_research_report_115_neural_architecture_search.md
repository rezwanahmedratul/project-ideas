# AI Research Report #115 — Neural Architecture Search & Automated ML

**Date:** 2026-09-09  
**Category:** AutoML

---

## Executive Summary

Neural Architecture Search (NAS) and automated machine learning (AutoML) have matured from academic curiosities to production tools. These systems can now design architectures that match or exceed human-engineered designs, while also automating hyperparameter tuning and pipeline optimization.

---

## What is NAS?

Neural Architecture Search automates the design of neural network architectures. Instead of manually crafting layers and connections, algorithms search the space of possible architectures to find optimal designs.

### Search Strategies

| Strategy | Description | Speed | Quality |
|----------|-------------|-------|---------|
| **Random Search** | Random sampling | Fast | Good |
| **Grid Search** | Exhaustive exploration | Slow | Best |
| **RL-based** | Reinforcement learning controller | Medium | Very Good |
| **Evolutionary** | Genetic algorithms | Medium | Good |
| **Gradient-based** | Differentiable search | Fast | Very Good |

---

## Notable NAS Discoveries

### EfficientNet (Google, 2019)
- Discovered compound scaling method
- Achieved better accuracy-efficiency tradeoff
- Still widely used in production

### EfficientNetV2 (2021)
- Training-aware hardware platform
- Faster training without accuracy loss

### Google's Once-for-All (2020)
- Single super-network containing all sub-networks
- One search, multiple deployments

---

## AutoML Platforms

### 1. Google AutoML
- **Vision:** Image classification, object detection
- **Natural Language:** Text classification, entity extraction
- **Tabular:** Prediction on structured data
- **Pricing:** Pay-per-use, no infrastructure management

### 2. AutoGluon (AWS)
- Multi-model ensemble automatically
- Supports tabular, image, text, time series
- Open source, runs on AWS or locally

### 3. Vertex AI (Google Cloud)
- End-to-end ML pipeline
- Automated model selection and tuning
- Integration with BigQuery, Kubernetes

### 4. H2O AutoML
- Open source, local or cloud deployment
- Wide algorithm support
- Explainability built-in

### 5. Ray AIR
- Distributed ML framework
- Scalable hyperparameter tuning
- Model serving integration

---

## NAS in Practice

### Workflow
```
┌─────────────┐
│  Dataset    │
└──────┬──────┘
       ▼
┌─────────────┐     ┌─────────────┐
│  Search     │────▶│  Evaluate   │
│  Algorithm  │     │  on验证 Set │
└─────────────┘     └──────┬──────┘
                           │
                    ┌──────┴──────┐
                    │  Better?    │
                    └──────┬──────┘
                           ▼
                    ┌─────────────┐
                    │  Save Best  │
                    └─────────────┘
```

### Code Example (PyTorch + NAS)
```python
import torch
from nasbench import api

# Define search space
graph_spec = nasbench.query(
    module_choices=['conv3x3', 'avg_pool3x3', 'max_pool3x3']
)

# Train and evaluate
model = build_nas_model(graph_spec)
accuracy = train_and_evaluate(model, train_data, val_data)
```

---

## Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| Computational cost | Weight sharing, early stopping |
| Transferability | Multi-task learning |
| Real-world constraints | Hardware-aware search |
| Interpretability | Architecture visualization |

---

## Future Directions

1. **Differentiable NAS:** End-to-end trainable architectures
2. **Zero-cost proxies:** Predict performance without training
3. **Neural predictors:** Surrogate models for search
4. **Federated NAS:** Distributed architecture search

---

## References

1. [EfficientNet Paper](https://arxiv.org/abs/1905.11946)
2. [NASBench Benchmark](https://github.com/google-research/nasbench)
3. [AutoGluon Documentation](https://auto.gluon.ai/)
4. [Ray AIR Guide](https://docs.ray.io/en/latest/train/index.html)

---

*Generated: 2026-09-09 | Source: Overnight research engine*
