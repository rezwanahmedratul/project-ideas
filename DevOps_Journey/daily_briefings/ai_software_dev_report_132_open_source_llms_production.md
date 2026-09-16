# AI Software Dev Report #132 — Open-Source LLMs for Production Deployment

## Overview
The open-weight LLM ecosystem has matured dramatically in 2025–2026, with models from Meta, Mistral AI, Qwen, and others providing production-grade alternatives to proprietary APIs. This report covers the leading open models, their licensing, deployment considerations, and trade-offs.

## Leading Open Models (2025–2026)

| Model | Developer | Size | License | Notable Features |
|-------|-----------|------|---------|------------------|
| Llama 3.3 70B | Meta | 70B (MoE) | Custom (permissive) | Strong reasoning, 128K context, excellent coding benchmarks |
| Llama 3.1 405B | Meta | 405B (MoE, 37B active) | Custom | Chain-of-thought specialization, SOTA open weights |
| Mistral Large 2 | Mistral AI | 123B | Apache 2.0 | 80+ languages, multilingual strength |
| Qwen 2.5 | Alibaba | 0.5B–72B series | Apache 2.0 | Strong open-source benchmark performance |
| Gemma 3 | Google DeepMind | Up to 27B | Gemma terms | Optimized for efficiency, strong reasoning |
| DeepSeek-V3 | DeepSeek | 671B (MoE, 37B active) | Custom | Cost-effective training, coding-focused |

## Licensing Landscape
- **Permissive** (Apache 2.0): Mistral Large, Qwen — safe for commercial use
- **Custom permissive**: Llama (Meta), Gemma (Google) — allowed commercially with restrictions
- **Proprietary**: DeepSeek varies by model — review terms carefully

## Deployment Options

### Local/Edge Inference
- **llama.cpp / Ollama** — GGUF quantization for CPU/GPU inference
- **vLLM** — High-throughput serving with PagedAttention
- **TensorRT-LLM** — NVIDIA-optimized inference

### Cloud API Wrappers
- Run open models via Replicate, Together AI, Hugging Face Inference Endpoints
- Self-host via Kubernetes + KServe or Cloud Run

## Production Considerations
1. **Cost vs. Control** — Open models eliminate API costs but require infra investment
2. **Fine-tuning** — LoRA/QLoRA enables cheap domain adaptation
3. **Quantization** — 4-bit/8-bit GGUF reduces memory by 4-8x with minimal quality loss
4. **Security** — Air-gapped deployments for sensitive workloads
5. **Evaluation** — Use lm-eval-harness for benchmarking before production deployment

## Reference Links
- [Mistral AI Models](https://docs.mistral.ai/models)
- [Open-Source LLM Comparison 2026](https://till-freitag.com/en/blog/open-source-llm-comparison)
- [Hugging Face — Best Open-Source LLMs 2026](https://huggingface.co/blog/daya-shankar/open-source-llms)
- [llama.cpp GitHub](https://github.com/ggerganov/llama.cpp)
- [vLLM Documentation](https://docs.vllm.ai/)
