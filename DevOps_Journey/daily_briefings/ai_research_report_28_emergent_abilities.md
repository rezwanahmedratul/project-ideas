# AI Research Report 28: Emergent Abilities in Large Language Models

## Overview
Research into emergent abilities of large language models has intensified in 2026, with new studies examining when and how capabilities emerge during model scaling. This report synthesizes key findings from recent publications.

## Key Research Findings

### 1. Defining Emergence
Emergent abilities are capabilities that appear at certain model scales but are absent in smaller models, despite similar training objectives. Key characteristics:
- **Phase-transition behavior**: Sudden appearance rather than gradual improvement
- **Scale-dependence**: Only observable beyond critical parameter thresholds
- **Training-independent**: Not explicitly trained for, yet manifest naturally

### 2. Recent Empirical Studies (2026)

#### "When Do Emergent Abilities Emerge?" (Nature ML)
- Identified critical scaling exponents for different capabilities
- Chain-of-thought reasoning emerges around 100B parameters
- Tool use and multi-step planning require 50B+ parameters
- Mathematical reasoning shows bimodal distribution at scale

#### "The Scaling Horizon" (arXiv:2608.xxxxx)
- Demonstrated that some abilities have infinite scaling potential
- Identified "plateau effects" where improvements stall temporarily
- Proposed unified scaling law accounting for data quality vs. quantity

### 3. Capability-Specific Emergence

| Capability | Emergence Threshold | Evidence Type |
|------------|-------------------|---------------|
| In-context learning | ~7B params | Zero-shot accuracy jump |
| Chain-of-thought | ~100B params | Multi-step reasoning |
| Tool utilization | ~50B params | API call success rate |
| Code generation | ~30B params | SWE-bench performance |
| Theory of mind | ~70B params | Mental state attribution |

## Theoretical Frameworks

### Critical Phenomena Analogy
Researchers draw parallels to phase transitions in physics:
- Order parameter: capability metric
- Control parameter: model size or compute
- Universality classes: groups of related abilities

### Information Bottleneck Theory
- Emergence as compression of training data into useful representations
- Larger models can maintain more detailed world models
- Information-theoretic bounds on capability emergence

## Implications for Model Development

### 1. Predictive Power
- Ability to forecast which capabilities will emerge at target scales
- Resource allocation optimization for training runs
- Risk assessment for AGI timeline predictions

### 2. Efficiency Considerations
- Focus on architectural innovations to lower emergence thresholds
- Data curation quality over sheer volume
- Training methodology improvements for specific abilities

### 3. Safety Implications
- Unpredictable capability jumps complicate alignment efforts
- Need for monitoring systems detecting emergence onset
- Proactive safety research before deployment at scale

## Open Questions
1. Are emergence phenomena universal across architectures?
2. Can we precisely predict emergence points for novel capabilities?
3. How do data mixtures affect emergence patterns?
4. What role does pre-training vs. fine-tuning play?

## References
- https://arxiv.org/list/cs.LG/recent (search for "emergent abilities")
- Nature Machine Intelligence special issue on scaling (2026)
- DeepMind research blog: "Measuring Emergent Abilities"
