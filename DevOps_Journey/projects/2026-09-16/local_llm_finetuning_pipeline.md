# Project: Local LLM Fine-Tuning Pipeline

## Overview
Build an end-to-end fine-tuning pipeline for open-source LLMs using LoRA/QLoRA, running entirely on local hardware. Includes dataset preparation, training, evaluation, and deployment.

## Architecture
```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  Dataset        │     │  Training       │     │  Evaluation     │
│  Collection     │────▶│  (LoRA/QLoRA)   │────▶│  ( benchmarks  │
│                 │     │                 │     │  + custom tests)│
│• Raw text/docs  │     │• Unsloth or     │     │                 │
│• Cleaning       │     │  Axolotl framework│   • TruthfulQA     │
│• Tokenization   │     │• GPU memory opt. │     • MMLU subset    │
└─────────────────┘     │• Quantization    │     • Custom evals   │
                        └────────┬────────┘     └────────┬────────┘
                                 │                       │
                                 ▼                       ▼
                        ┌─────────────────┐     ┌─────────────────┐
                        │  Model          │     │  Serving        │
                        │  Registry       │     │  (Ollama/vLLM)  │
                        │                 │     │                 │
                        │• Base model     │◄────│• API endpoint   │
                        │• Adapter weight │     │• Streaming      │
                        │• Metadata       │     │• Rate limiting  │
                        └─────────────────┘     └─────────────────┘
```

## Workflow
1. Collect and clean domain-specific training data
2. Choose base model (Llama 3, Mistral, Qwen)
3. Convert to alpaca/train format
4. Run QLoRA fine-tuning with 4-bit quantization
5. Evaluate on held-out test set
6. Package adapter for deployment
7. Serve via Ollama or vLLM

## Tools & Tech Stack
- **Unsloth** — Memory-efficient training (2x faster, 60% less VRAM)
- **Axolotl** — Declarative training config
- **Hugging Face Transformers** — Model loading
- **PEFT** — Parameter-efficient fine-tuning (LoRA)
- **bitsandbytes** — 4-bit quantization
- **Ollama** — Local model serving
- **vLLM** — High-throughput inference
- **lm-eval-harness** — Benchmarking

## Learning Goals
- LoRA vs full fine-tuning trade-offs
- QLoRA 4-bit quantization techniques
- Dataset curation and formatting
- Training hyperparameter tuning
- Model evaluation methodologies
- Local model serving patterns

## Build Milestones
1. [ ] Set up training environment (GPU driver, CUDA)
2. [ ] Prepare synthetic training dataset
3. [ ] Load base model and run inference baseline
4. [ ] Implement QLoRA fine-tuning script
5. [ ] Train adapter on subset of data
6. [ ] Evaluate with lm-eval-harness
7. [ ] Deploy via Ollama and test API responses

## Reference Links
- [Unsloth Documentation](https://docs.unsloth.ai/)
- [Axolotl Training Framework](https://github.com/axolotl-ai-cloud/axolotl)
- [PEFT Library](https://huggingface.co/docs/peft)
- [lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness)
