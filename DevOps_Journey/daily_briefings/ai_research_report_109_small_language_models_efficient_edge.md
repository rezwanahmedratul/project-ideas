# AI Research Report #109: Small Language Models and Efficient Deployment at the Edge

**Date:** 2026-09-08  
**Topic:** Making powerful AI accessible through model compression, distillation, and edge deployment

---

## Executive Summary

While frontier labs race to build trillion-parameter models, a parallel revolution in small language models (SLMs) is making AI accessible everywhere. From smartphones to IoT devices, efficient models are enabling on-device intelligence with privacy, latency, and cost advantages that cloud-only approaches cannot match.

---

## The SLM Revolution

### Model Size Spectrum (2026)

| Category | Parameter Range | Examples | Use Cases |
|----------|-----------------|----------|-----------|
| Tiny | < 1B | Phi-3-mini, Gemma-2b | Mobile, IoT |
| Small | 1-7B | Llama 3.2, Qwen 2.5 | Laptops, edge servers |
| Medium | 7-70B | Llama 3.1-70B, Mistral Large | Cloud inference, fine-tuning |
| Large | 70B-400B | Claude Sonnet, Gemini Pro | Cloud production |
| Frontier | 400B+ | Claude Opus, Gemini Ultra | Research, specialized tasks |

### Performance vs. Size Trade-offs

| Model | Parameters | MMLU Score | Inference Cost (per 1K tokens) |
|-------|------------|------------|--------------------------------|
| Llama 3.2 1B | 1B | 58.3% | $0.001 |
| Llama 3.2 3B | 3B | 65.7% | $0.003 |
| Llama 3.2 8B | 8B | 73.2% | $0.008 |
| Llama 3.1 70B | 70B | 82.4% | $0.065 |
| Claude Sonnet 4 | ~175B* | 87.1% | $0.30 |

_*Estimated effective parameters_

---

## Compression Techniques

### Quantization Methods

| Technique | Bit Depth | Accuracy Loss | Speedup |
|-----------|-----------|---------------|---------|
| FP16 (baseline) | 16-bit | 0% | 1x |
| INT8 | 8-bit | 1-2% | 2x |
| INT4 | 4-bit | 3-5% | 4x |
| NF4 (QLoRA) | 4-bit (non-uniform) | 1-2% | 4x |

### Distillation Approaches

1. **Teacher-Student Distillation**: Large model teaches smaller model
2. **Self-Distillation**: Model learns from its own predictions
3. **Knowledge Transfer**: Transfer specific capabilities without full distillation
4. **Prompt-Based Compression**: Encode knowledge in prompts rather than weights

---

## Edge Deployment Strategies

### On-Device Inference
- **Smartphones**: Apple Neural Engine, Snapdragon AI
- **Laptops**: Core ML, OpenVINO, ONNX Runtime
- **IoT**: TinyML frameworks, WebLLM

### Hybrid Approaches
- Local preprocessing → Cloud reasoning → Local post-processing
- Split inference across device and edge server
- Dynamic model selection based on available resources

---

## Reference Links

- [Microsoft Phi Models](https://www.microsoft.com/en-us/research/project/phi/)
- [Google Gemma Models](https://ai.google.dev/gemma)
- [Qwen Team Models](https://qwenlm.github.io/)
- [TinyML Foundation](https://www.tinyml.org/)

---

*Report generated: 2026-09-08 | AI Research Series #109*
