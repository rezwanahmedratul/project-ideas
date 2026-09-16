# AI Software Dev Report #102 — MLOps Infrastructure & Model Deployment Pipelines

## Overview
As LLMs and ML models become central to software products, MLOps infrastructure has evolved to handle training, serving, monitoring, and iteration at scale. The focus has shifted from standalone model serving to integrated CI/CD/CT (Continuous Training) pipelines.

## Modern MLOps Stack

### Training & Experiment Tracking
- **MLflow** — Experiment tracking, model registry, deployment packaging
- **Weights & Biases (W&B)** — Sweeps, dashboard, dataset versioning
- **DVC** — Data version control integrated with Git pipelines
- **Kubeflow** — Kubernetes-native ML workflow orchestration

### Model Serving
- **vLLM** — High-throughput LLM serving with PagedAttention, OpenAI-compatible API
- **Triton Inference Server** — NVIDIA's multi-framework inference server
- **Ollama + llama.cpp** — Local GGUF model serving for edge/on-prem use cases
- **KServe** — Kubernetes-based serving with autoscaling and canary deployments

### Monitoring & Observability
- **Prometheus + Grafana** — Metric collection and dashboards
- **Evidently AI** — Model drift detection and data quality monitoring
- **WhyLabs** — Production LLM observability platform

## Key Trends 2025–2026
1. **LLMOps as distinct discipline** — Separate from traditional MLOps due to prompt management, token cost tracking, and non-deterministic outputs
2. **Fine-tuning automation** — LoRA/QLoRA pipelines enabling cheap, iterative model adaptation
3. **Edge deployment** — Small Language Models (SLMs) running on consumer hardware
4. **Automated evaluation** — Benchmarks like lm-eval-harness integrated into CI gates

## Architecture: End-to-End Pipeline
```
Data → Version Control (DVC) → Training (PyTorch/JAX) → 
Experiment Tracking (MLflow/W&B) → Registry → 
Serving (vLLM/Triton) → Monitoring (Prometheus/Grafana) → Feedback Loop
```

## Reference Links
- [vLLM — High-Throughput LLM Serving](https://docs.vllm.ai/)
- [MLflow Documentation](https://mlflow.org/docs/latest/)
- [Weights & Biases](https://wandb.ai/site)
- [DVC — Data Version Control](https://dvc.org/)
- [lm-eval-harness](https://github.com/EleutherAI/lm-evaluation-harness)
