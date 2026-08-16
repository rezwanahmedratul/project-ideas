# Fine-Tuned Python Docstring Generator

## Overview
Fine-tune an open-source LLM (Phi-3 or Gemma) to generate accurate Python docstrings from function signatures and bodies. Use LoRA/QLoRA for efficient training.

## Architecture
```
Training Data (Function → Docstring pairs)
    ↓
QLoRA Fine-tuning (Unsloth)
    ↓
Trained Model (GGUF export)
    ↓
Inference API (vLLM or llama.cpp)
    ↓
IDE Extension / CLI Tool
```

## Workflow
1. Collect Python code dataset with existing docstrings
2. Format as instruction-tuning data
3. Fine-tune Phi-3-mini using QLoRA
4. Export to GGUF for local inference
5. Build CLI tool that analyzes .py files
6. Generate and apply docstrings automatically

## Tools
- Python (transformers, peft, unsloth)
- Phi-3-mini or Gemma 2B
- vLLM for serving
- Python AST module for parsing

## Learning Goals
- Parameter-efficient fine-tuning (PEFT)
- LoRA/QLoRA techniques
- Instruction tuning methodology
- Local model deployment

## Build Milestones
- [ ] Prepare training dataset
- [ ] Run QLoRA fine-tuning (single GPU)
- [ ] Export GGUF model
- [ ] Build inference CLI
- [ ] Add AST-based docstring insertion
- [ ] Evaluate with automated metrics

## References
- https://sivaro.in/articles/best-open-source-models-to-fine-tune-in-2026-a-field-guide/
- https://unsloth.ai/
- https://huggingface.co/docs/peft/
