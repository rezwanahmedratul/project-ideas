# AI Software Dev Report #139 — AI Model Compression: Pruning, Quantization & Distillation

## Overview
As AI models grow larger, compression techniques become essential for deployment on resource-constrained devices and reducing inference costs. In 2025, advanced pruning, quantization, and distillation methods enable 10-100x model size reduction with minimal accuracy loss.

## Compression Techniques Overview

### Quantization
Reducing numerical precision of model weights and activations.

| Method | Precision | Speedup | Memory Reduction | Accuracy Impact |
|--------|-----------|---------|------------------|-----------------|
| **FP32 → FP16** | Half float | 2x | 2x | Near-zero |
| **FP32 → INT8** | 8-bit integer | 4x | 4x | 1-3% |
| **FP32 → INT4** | 4-bit integer | 8x | 8x | 5-10% |
| **FP32 → NF4** | NormalFloat 4-bit | 8x | 8x | <1% |

**Key approaches:**
- **PTQ (Post-Training Quantization)** — Quantize without retraining
- **QAT (Quantization-Aware Training)** — Simulate quantization during training
- **SmoothQuant** — Balance activation/weight quantization difficulty
- **AWQ (Activation-aware Weight Quantization)** — Preserve important weights

### Pruning
Removing redundant parameters from trained models.

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Dense         │     │   Structured    │     │   Sparse        │
│   Model         │────▶│  Pruning        │────▶│   Model         │
│                 │     │                 │     │                 │
│ All weights     │     │ Remove entire   │     │ Zero-weight     │
│ active          │     │ rows/cols/head  │     │ masking         │
│                 │     │ (channels)      │     │ + compression   │
└─────────────────┘     └─────────────────┘     └─────────────────┘
```

| Technique | Description | Typical Reduction |
|-----------|-------------|-------------------|
| **Magnitude pruning** | Remove smallest weights | 50-90% |
| **Structured pruning** | Remove channels/layers | 2-4x |
| **Neural Architecture Search** | Discover optimal sparse structure | Task-dependent |
| **Lottery Ticket Hypothesis** | Find winning subnetworks | Varies |

### Knowledge Distillation
Training smaller "student" models to mimic larger "teacher" models.

```
Teacher Model (Large)          Student Model (Small)
┌────────────────────────┐     ┌────────────────────────┐
│  LLM-70B / GPT-4       │     │  LLM-7B / distilled    │
│  • Full precision       │     │  • INT8 quantized       │
│  • 128 layers           │     │  • 24 layers            │
│  • 1M+ tokens context   │     │  • 32K tokens context   │
└──────────┬─────────────┘     └──────────┬─────────────┘
           │                               │
           │     Distillation Loss         │
           │     (logits + features)       │
           └───────────►◄──────────────────┘
                       Training
```

**Distillation variants:**
- **Logit distillation** — Match output probability distributions
- **Feature distillation** — Match intermediate layer representations
- **Attention distillation** — Transfer attention patterns
- **Sequence-level distillation** — Fine-tune on teacher-generated data

## Combined Approaches

### Sequential Pipeline
```
Original Model
     │
     ▼
 [Pruning] → Reduced architecture
     │
     ▼
 [Distillation] → Compressed weights
     │
     ▼
 [Quantization] → INT8/INT4 deployment
     │
     ▼
Edge Deployable Model (10-100x smaller)
```

### Joint Optimization
- **RT-LLM** — Combined pruning and quantization for LLMs
- **GPTQ** — One-shot quantization with Hessian approximation
- **SmoothQuant** — Balanced quantization for LLM inference

## Tools & Libraries

### Pruning
- **PyTorch Pruning** — Built-in module
- **TensorFlow Model Optimization** — Pruning + quantization
- **Hugging Face Optimum** — Easy compression pipelines

### Quantization
- **TensorRT** — NVIDIA's optimization engine
- **ONNX Runtime** — Cross-platform quantization
- **bitsandbytes** — 4-bit/8-bit quantization for PyTorch
- **AutoGPTQ** — GPTQ implementation for transformers

### Distillation
- **LangChain distillation** — Fine-tune small models on large model outputs
- **DistilBERT-style** — Knowledge distillation for BERT-class models
- **TinyLlama** — Distilled 1.1B LLM achieving 7B performance

## Performance Benchmarks (2025)

### LLaMA-3 8B Compression Results
| Method | Size | Speed | MMLU Score |
|--------|------|-------|------------|
| Original FP16 | 16 GB | 1x | 66.1% |
| INT8 Quantized | 8 GB | 2x | 65.3% |
| INT4 Quantized | 4 GB | 4x | 62.8% |
| Pruned 50% + INT8 | 6 GB | 2.5x | 64.9% |
| Distilled + Quantized | 5 GB | 3x | 63.2% |

### Mobile Deployment
- **MobileBERT** — 4x smaller than BERT, similar accuracy
- **TinyBERT** — Layer-wise distillation for BERT
- **DistilWhisper** — 40% smaller speech recognition model

## Reference Links
- [AI Model Compression 2025](https://tensorblue.com/blog/ai-model-compression-pruning-quantization-knowledge-distillation-2025)
- [Awesome LLM Compression GitHub](https://github.com/HuangOwen/Awesome-LLM-Compression)
- [LLM 101: Model Compression](https://antreas.io/documents/teaching/llm101/llm-101-model-compression-slides.pdf)
- [Knowledge Distillation Guide 2026](https://www.articsledge.com/post/knowledge-distillation)
