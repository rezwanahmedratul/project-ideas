# AI Research Report #143 — Hallucination Mitigation in Large Language Models

## Overview
Hallucination — the generation of factually incorrect or fabricated information — remains one of the most persistent challenges in LLM deployment. Research in 2025 has produced a rich taxonomy of mitigation techniques spanning prompting, verification, and architectural approaches.

## Taxonomy of Hallucination Types

### Model-Intrinsic Hallucinations
- Generated content contradicting model's own training knowledge
- Often triggered by ambiguous prompts or insufficient context
- Example: Confidently stating false historical facts

### Factuality Hallucinations
- Contradicting verifiable external information
- Most dangerous for production systems
- Example: Fabricating paper citations, legal precedents

### Logical Hallucinations
- Internal inconsistencies within generated output
- Reasoning errors despite plausible surface structure
- Example: Mathematical proof with flawed steps

## Mitigation Techniques

### Prompt Engineering
1. **Chain-of-Thought (CoT)** — Structured reasoning guides evidence-based conclusions
2. **Self-Consistency** — Generate multiple reasoning paths, select majority answer
3. **Constrained decoding** — Restrict output to known factual spaces
4. **Retrieval-augmented prompting** — Ground responses in verified sources

### Post-Generation Safeguards
1. **Fact-checking systems** — Cross-reference claims against knowledge bases
2. **LLM-as-judge** — Use secondary model to score faithfulness
3. **Best-of-N selection** — Generate candidates, evaluate and select most faithful (ACL Findings 2025)
4. **Self-verification loops** — Model critiques its own output iteratively

### Detection Methods
| Approach | Mechanism | Latency Cost |
|----------|-----------|--------------|
| **Linguistic cues** | Detect hedging language, over-confidence patterns | Low |
| **Latent signal probing** | Analyze internal activation patterns | Medium |
| **Lightweight classifiers** | Fine-tuned models flag hallucination probability | Low-Medium |
| **Agentic frameworks** | Multi-agent consultation for verification | High |

### Architectural Approaches
- **RAG integration** — Always ground generation in retrieved context
- **Knowledge graph grounding** — Link outputs to structured knowledge
- **Constitutional AI** — Self-critique based on predefined principles
- **Uncertainty quantification** — Calibrate confidence scores for detection

## Evaluation Metrics
- **FactCC**: Factual consistency scoring
- **QNLI**: Question-answering NLI accuracy
- ** Faithfulness**: Generated claims supported by source context
- **Contextual Recall**: Relevant context retrieval rate

## Reference Links
- [MDPI — Hallucination Mitigation Taxonomic Survey](https://www.mdpi.com/2673-2688/6/10/260)
- [Lakera — LLM Hallucinations Guide 2026](https://www.lakera.ai/blog/guide-to-hallucinations-in-large-language-models)
- [InfoMineo — Stop AI Hallucinations Guide](https://infomineo.com/artificial-intelligence/stop-ai-hallucinations-detection-prevention-verification-guide-2025/)
- [ACL Findings 2025 — Mitigating Hallucination via Best-of-N](https://aclanthology.org/2025.findings-acl.752.pdf)
- [Frontiers in AI — Factuality Scorers and Feedback Loops](https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2025.1622292/pdf)
