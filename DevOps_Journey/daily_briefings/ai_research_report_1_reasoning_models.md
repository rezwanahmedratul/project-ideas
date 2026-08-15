# Report 1: Reasoning Models & Test-Time Compute Scaling — The 2025 Paradigm Shift

**Date:** August 7, 2026  
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
- **Emergent Behaviors:** Self-verification, backtracking, extended thinking, "aha!" moments — **not programmed, emerged from RL**

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
Stage 4: RL for Helpfulness/Safety (alignment)
    ↓
**DeepSeek-R1**
```

#### Benchmark Results (DeepSeek-R1 vs. OpenAI o1)
| Benchmark | DeepSeek-R1 | OpenAI o1 | Significance |
|-----------|-------------|-----------|--------------|
| **AIME 2024** | **79.8%** | 79.2% | Math olympiad level |
| **MATH-500** | **97.3%** | 96.4% | Competition math |
| **Codeforces Elo** | **2029** | 1891 | **Expert human level** |
| **GPQA Diamond** | 71.5% | 75.7% | PhD-level science |
| **SWE-bench Verified** | ~82% (with agent) | ~85% (with agent) | Real-world coding |

#### Impact Beyond Benchmarks
1. **Open Weights + Open Recipe:** Released model + training methodology → 50+ reproductions in weeks
2. **Proved RL > Supervised CoT:** Reasoning can be *incentivized*, not just *taught*
3. **Cost Efficiency:** Frontier reasoning at fraction of proprietary training cost
4. **Distillation Works:** R1-distilled smaller models (1.5B–70B) retain strong reasoning

---

## 3. Test-Time Compute Scaling: The Economic Paradigm Shift

### The Core Discovery (Convergent Finding Across 10+ Papers, 2025)
> **"Spending more compute at inference often outperforms training a bigger model."**

### Mechanisms
| Technique | Description | Compute Cost | Gain |
|-----------|-------------|--------------|------|
| **Process Reward Models (PRMs)** | Score each reasoning step, not just final answer | 2–10x | +10–30% on reasoning |
| **Beam Search over Chains** | Explore N reasoning paths, keep best | Nx | +5–20% |
| **Monte Carlo Tree Search (MCTS)** | Tree search in reasoning space | 10–100x | +15–40% |
| **Self-Consistency / Majority Voting** | Sample K times, vote on answer | Kx | +5–15% |
| **Self-Correction / Reflection** | Model critiques own output, iterates | 2–5x | +10–25% |
| **Tree of Thoughts / Graph of Thoughts** | Structured exploration | 10–100x | +20–50% |

### Economic Implications
| Scenario | Traditional Approach | Test-Time Scaling Approach |
|----------|---------------------|---------------------------|
| **Need better reasoning** | Train 10x larger model ($10M–$1B+) | Run smaller model with 10x inference compute ($10K–$100K) |
| **Deployment Cost** | High fixed (model size) | Variable (pay per reasoning task) |
| **Latency** | Single forward pass | Multi-pass (configurable budget) |
| **Accessibility** | Requires massive training cluster | Runs on single GPU / consumer hardware |

### Key Quote (Widely Cited, 2025)
> *"Test-time compute scaling may be the single most important research finding of the year. It changes the economics of AI capability: you don't always need a bigger model — you need a smarter inference strategy."*

---

## 4. Training Methodologies for Reasoning (2025 Survey)

### Taxonomy (from arXiv:2503.22732)
| Category | Methods | Examples |
|----------|---------|----------|
| **Inference-Time Scaling** | PRM, Beam Search, MCTS, Self-Consistency, ToT, GoT | o1, R1-inference, various wrappers |
| **Reinforcement Learning** | GRPO, PPO, RLVR, CGPO, APO, DPO, RLAIF | DeepSeek-R1, Phi-4, Tülu 3 |
| **Supervised Fine-Tuning** | CoT distillation, Rejection Sampling, Iterative SFT | WizardLM, Orca, Starling |
| **Distillation** | Reasoning distillation from LRM → smaller model | DeepSeek-R1-Distill, Phi-4 distill |
| **Self-Improvement** | Model generates own training data, verifies, retrains | STaR, ReST, Self-Rewarding LM |
| **Retrieval-Augmented** | RAG + Reasoning (Search-o1, RAG-CoT) | Search-o1, RAPTOR |
| **Multi-Agent** | Debate, Collaboration, Verification | Multi-Agent Debate, Society of Minds |

### Emerging Best Practices (Late 2025)
1. **Cold Start SFT → RL → Polish SFT → Alignment RL** (R1 recipe)
2. **Verifiable Rewards are King:** Math, code execution, unit tests > subjective preferences
3. **GRPO > PPO for Reasoning:** No critic model needed; more stable; less memory
4. **Distillation Preserves Reasoning:** Small models can inherit reasoning patterns
5. **Synthetic Data Quality > Quantity:** Phi-4 proved 14B + synthetic > 70B + web data

---

## 5. Open Problems & Challenges (arXiv:2503.22732, Section VII)

### Challenge 1: Multi-Step Reasoning Without Human Supervision
- **Problem:** Current RL requires verifiable rewards (math/code). Open-ended reasoning lacks ground truth.
- **Directions:** AI feedback (RLAIF), learned verifiers, process-based rewards.

### Challenge 2: Robustness in Chained Task Execution
- **Problem:** Errors propagate in long reasoning chains; "overthinking" degrades performance.
- **Directions:** Confidence calibration, early exit, verification checkpoints.

### Challenge 3: Balancing Structured Prompting with Generative Flexibility
- **Problem:** Rigid CoT formats limit creativity; free-form reasoning is hard to verify.
- **Directions:** Flexible reasoning schemas, structured output with escape hatches.

### Challenge 4: Long-Context Retrieval + External Tool Integration
- **Problem:** Reasoning over 1M+ tokens + tool use = compounding errors.
- **Directions:** Hierarchical reasoning, memory-augmented architectures, better tool schemas.

### Challenge 5: Evaluation of Reasoning Quality
- **Problem:** Benchmarks saturate; real-world reasoning ≠ benchmark reasoning.
- **Directions:** Human preference eval, open-ended tasks, process-based evaluation.

---

## 6. Strategic Implications for 2026–2027

### For Model Builders
- **Invest in RL Infrastructure:** GRPO/RLVR pipelines, verifiable reward environments
- **Build Reasoning Eval Suites:** Beyond benchmarks — process evaluation, real tasks
- **Optimize Inference Stack:** Speculative decoding, KV cache compression (MLA), batched reasoning

### For Application Developers
- **Design for Reasoning Budgets:** Explicit "think longer" knobs for hard problems
- **Use Smaller Models + More Inference:** Distilled R1/Qwen + PRM/beam search > large model single-pass
- **Build Verifiable Reward Functions:** For your domain (tests, lint, type-check, business rules)

### For Researchers
- **Open Problems:** Unsupervised reasoning, robustness, long-horizon, multimodal reasoning
- **New Paradigms:** Neurosymbolic, self-improving, federated reasoning

---

## Reference Links

1. **AIssential** — "Best AI Research Papers of 2025: Breakthroughs Worth Reading" — https://aissential.tech/blog/best-ai-research-papers-2025
2. **arXiv:2501.12948** — "DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning" — https://arxiv.org/abs/2501.12948
3. **arXiv:2412.14197** — "DeepSeek-V3 Technical Report" — https://arxiv.org/abs/2412.14197
4. **arXiv:2503.22732** — "Reasoning Beyond Limits: Advances and Open Problems for LLMs" — https://arxiv.org/html/2503.22732
5. **Google Research Blog** — "Google's year in review: 8 areas with research breakthroughs in 2025" — https://blog.google/innovation-and-ai/products/2025-research-breakthroughs/
6. **OpenAI** — "Learning to Reason with LLMs (o1/o3 blog posts)" — https://openai.com/research/
7. **DeepSeek** — "DeepSeek-R1 Blog / Technical Details" — https://github.com/deepseek-ai/DeepSeek-R1
8. **Analytics Vidhya** — "Top 10 AI Research Papers of 2025" — https://www.analyticsvidhya.com/blog/2026/05/top-ai-research-papers-of-2025/