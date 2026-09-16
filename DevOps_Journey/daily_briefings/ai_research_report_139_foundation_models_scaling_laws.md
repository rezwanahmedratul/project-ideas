# AI Research Report #139 — Foundation Models: Scaling Laws & Frontiers of Intelligence

## Overview
Scaling laws have guided the development of foundation models since Kaplan et al.'s seminal 2020 work demonstrated predictable relationships between model size, dataset size, and loss. In 2025, research has refined these laws for multimodal and reasoning-capable models while exploring whether scaling alone can achieve AGI or if architectural breakthroughs are needed.

## Key Findings on Scaling Laws

### Classic Power Laws
- Loss decreases as a power law with compute, parameters, and training data
- Chinchilla-optimality: equal tokens and parameters for optimal efficiency
- "It's so dumb it works" — simplicity of power laws despite model complexity

### Emerging Insights (2024–2025)
1. **Emergent Abilities** — Capabilities appear abruptly at certain scales (e.g., chain-of-thought reasoning, instruction following) rather than gradually
2. **Data Efficiency Frontier** — New architectures (Mamba, RWKV) challenge transformer scaling assumptions
3. **Multimodal Scaling** — Cross-modal alignment benefits from joint scaling of vision and language
4. **Reasoning Scaling** — o1-style models show that more compute during inference (not just training) unlocks new capabilities

### The "New Era" of Scaling (2025)
Recent research suggests scaling isn't over but evolving:
- **Compute allocation shifts**: 40% of compute to public models, 60% to inference/experiments in 2025–2026; shifting to 30/70 by 2027–2028
- **Domain-specific scaling**: Financial models showing effective scaling at lower token budgets (7B–70B range)
- **Architectural innovations**: Mixture-of-Experts, sparse attention reducing compute per token

## Foundation vs. Frontier Models
| Aspect | Foundation Models | Frontier Models |
|--------|-------------------|-----------------|
| Definition | Base layer for adaptation | Pushing capability boundaries |
| Access | Often open-weight | Usually proprietary |
| Examples | Llama, Mistral, Qwen | GPT-4/5, Gemini, Claude Opus |
| Use Case | Fine-tuned for specific tasks | General-purpose, state-of-the-art |

## Legal & Policy Dimensions
The distinction between foundation and frontier models matters for regulation:
- EU AI Act differentiates GPAI models by "systemic impact"
- US EO references "frontier models" with enhanced safety requirements
- Definitions remain contested — no universal threshold exists

## Reference Links
- [Scaling Laws Paper (Kaplan et al.)](https://arxiv.org/abs/2001.08361)
- [AI Model Scaling Isn't Over: New Era](https://aibusiness.com/language-models/ai-model-scaling-isn-t-over-it-s-entering-a-new-era)
- [Scaling Laws & Foundation Models PDF](https://elias-ai.eu/wp-content/uploads/2025/07/02-Open-fundation-models-scaling-laws-and-generalization-Jenia-Jitsev.pdf)
- [Foundation vs Frontier Models Explained](https://arxiv.org/pdf/2504.16138)
