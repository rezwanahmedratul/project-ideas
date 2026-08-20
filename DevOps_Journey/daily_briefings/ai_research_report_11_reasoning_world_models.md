# Report 11: Reasoning Models and World Models — The 2025 Paradigm Shift

**Date:** August 20, 2026  
**Category:** General AI Research Breakthroughs  
**Sources:** AIssential (2026), arXiv:2503.22732, DeepSeek-R1 Paper, Google Research Blog (2025), Multiple 2025 Papers

---

## Executive Summary

**2025 was the year reasoning became a first-class capability.** The emergence of Large Reasoning Models (LRMs) — OpenAI's o1/o3, DeepSeek-R1, Qwen-QwQ — and the discovery of **test-time compute scaling** fundamentally changed the AI capability curve. Reasoning is no longer an emergent property of scale; it's a trainable, scalable capability achievable through reinforcement learning and inference-time computation.

---

## 1. The LRM Revolution: From Chat to Reasoning

### What Are Large Reasoning Models (LRMs)?
Models that **interpose a chain of internal "thought" steps** between input and output, decomposing complex problems into methodical, stepwise reasoning before producing the final answer.

```
Standard LLM:           Input → [Forward Pass] → Output
Reasoning LRM:          Input → [Thought 1] → [Thought 2] → ... → [Thought N] → Output
                        (CoT / Reasoning Trace)
```

### Key LRMs of 2025
| Model | Release | Org | Key Innovation | Benchmark Highlights |
|-------|---------|-----|----------------|---------------------|
| **o1 / o3** | 2024/2025 | OpenAI | Large-scale RL for reasoning | 83.3% AIME, 2727 Codeforces |
| **DeepSeek-R1** | Jan 2025 | DeepSeek | **GRPO: RL without supervised CoT** | **79.8% AIME, 97.3% MATH, 2029 CF** |
| **Qwen-QwQ** | 2025 | Alibaba | Reasoning via RL | Competitive with o1 |
| **Gemini 2.5 / 3** | 2025 | Google | Native reasoning + multimodal | 23.4% MathArena Apex |
| **Nemotron 3 Ultra** | 2025 | NVIDIA | Reasoning optimized | Strong coding/math |

---

## 2. DeepSeek-R1: The Watershed Moment

### Why R1 Changed Everything
**Paper:** "DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning" (arXiv:2501.12948)

#### Core Innovation: Group Relative Policy Optimization (GRPO)
- **No Supervised CoT Data Required:** Unlike prior approaches (STaR, Rejection Sampling), R1 learns reasoning **purely from RL on verifiable rewards**
- **Reward Signal:** Correctness on math/code problems (verifiable by execution)
- **Emergent Behaviors:** Self-verification, backtracking, decomposition — **not programmed, emerged from RL**

#### Training Pipeline
```
Base Model (DeepSeek-V3)
    ↓
Stage 1: Cold Start (SFT on small high-quality CoT data)
    ↓
Stage 2: **Reasoning-Oriented RL (GRPO)**
    ├─ Generate multiple responses per prompt
    ├─ Score by verifiable reward (correctness)
    ├─ GRPO: Relative ranking within group (no critic model needed)
    └─ Update policy → longer, more coherent reasoning chains
    ↓
Stage 3: Rejection Sampling + SFT (polish)
    ↓
Final R1 Model
```

#### Results That Shocked the Community
- **79.8% on AIME 2024** (vs. o1's 83.3%) — close to frontier while being **open weights**
- **97.3% on MATH-500** — near-perfect on competition math
- **Cost:** ~$557K for training vs. OpenAI's estimated $6M+ — **10x cheaper**
- **Open Weights:** Available for research and commercial use

---

## 3. Test-Time Compute Scaling

### The Discovery
**Key insight:** Reasoning quality scales with **inference-time computation**, not just training-time FLOPs. You can "think longer" at inference to solve harder problems.

#### Evidence
- **o1-preview** used ~10x more推理 tokens than GPT-4
- **DeeperSearch** (Tiang et al., 2025): Scaling search depth linearly improves QA performance
- **Nasiryan et al. (2025):** Verbalized exploration scales predictably with test-time compute
- **Self-Consistency (Wang et al.):** Sampling multiple reasoning paths and voting improves accuracy

### Practical Implications
| Strategy | How It Works | Benefit |
|----------|--------------|---------|
| **Longer CoT** | Allow more reasoning tokens | Better math/problem-solving |
| **Self-Consistency** | Sample N responses, vote | Robustness to randomness |
| **Tree of Thought** | Explore branching reasoning paths | Better for complex planning |
| **Verification Loop** | Generate → Verify → Revise | Higher correctness |

---

## 4. The Democratization of Reasoning

### Open Models Catch Up
- **Qwen2.5-Math / QwQ:** Strong open reasoning models
- **Llama-3.1-70B/405B + RL:** Fine-tuned for reasoning
- **DeepSeek-R1-Distill:** Smaller distilled versions (7B, 8B, 14B, 32B)
- **Olamo, Gemma:** Google's open reasoning-capable models

### Impact
- **No longer requires $100M+ budgets** to achieve reasoning capabilities
- **Local deployment possible** with quantized 7B-14B models
- **Cost per token drops dramatically** as distillation improves

---

## 5. Applications Beyond Math

While benchmarks focus on math, reasoning models excel at:
- **Code generation:** Multi-file edits, bug fixes, refactoring
- **Scientific discovery:** Hypothesis generation, experiment design
- **Legal analysis:** Contract review, case law reasoning
- **Medical diagnosis:** Symptom analysis, treatment recommendation
- **Strategic planning:** Market analysis, resource allocation

---

## 6. Open Questions and Future Directions

### The "Why" of Emergence
- Why do reasoning behaviors emerge from RL on verifiable rewards?
- Is there a critical threshold of model size for reasoning emergence?
- Can we intentionally engineer reasoning capabilities?

### Scaling Laws
- How does reasoning quality scale with model size, data, and test-time compute?
- Are there diminishing returns?
- What's the optimal balance between pre-training and RL?

### Alignment and Safety
- Can reasoning models be aligned as effectively as chat models?
- Risk of "deceptive alignment" in highly capable reasoners
- Need for new interpretability techniques

---

## References

1. DeepSeek-R1 Paper: "DeepSeek-R1: Incentivizing Reasoning Capability" - arXiv:2501.12948
2. Google Research Blog: "Reasoning Models" (2025)
3. "Scaling Test-Time Compute" - Tiang et al. (2025)
4. OpenAI o1 System Card
5. Qwen Technical Report: "Qwen2.5-Math"
6. AIssential: "Reasoning vs. Knowing in LLMs" (2026)
