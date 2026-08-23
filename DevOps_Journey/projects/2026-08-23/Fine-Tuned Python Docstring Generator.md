# Fine-Tuned Python Docstring Generator

**Category:** AI/ML  
**Date:** 2026-08-23

---

## Overview

Fine-tune a small open-source LLM to generate high-quality Python docstrings from function signatures and bodies. Trained on existing well-documented codebases, the model learns NumPy, Google, and Sphinx docstring styles. Deploy as a VS Code extension or CLI tool.

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│         Docstring Generator Pipeline                 │
│                                                     │
│  ┌──────────┐    ┌──────────────┐    ┌───────────┐  │
│  │  Input   │───▶│  Preprocess  │───▶│  Tokenize │  │
│  │  Code    │    │  (AST parse) │    │           │  │
│  └──────────┘    └──────────────┘    └─────┬─────┘  │
│                                             │         │
│                                    ┌────────▼─────┐  │
│                                    │  Fine-Tuned  │  │
│                                    │  Model       │  │
│                                    │  (Qwen2.5    │  │
│                                    │   1.5B/3B)   │  │
│                                    └──────┬───────┘  │
│                                           │           │
│                                    ┌──────▼───────┐  │
│                                    │  Post-process│  │
│                                    │  (format)    │  │
│                                    └──────┬───────┘  │
│                                           │           │
│                                    ┌──────▼───────┐  │
│                                    │  Output      │  │
│                                    │  (docstring) │  │
│                                    └──────────────┘  │
└─────────────────────────────────────────────────────┘
```

---

## Workflow

1. **Parse** Python file using AST to extract functions/classes
2. **Format** signature + body as model input
3. **Generate** docstring using fine-tuned model
4. **Validate** output against docstring style guides
5. **Insert** docstring back into source code
6. **Save** with backup of original

---

## Tools & Stack

| Component | Technology |
|-----------|-----------|
| Base Model | Qwen2.5-1.5B or Llama 3.2-3B (GGUF) |
| Training | Hugging Face Transformers + PEFT |
| Dataset | NumPy-style docstrings from popular libraries |
| Inference | llama.cpp or vLLM |
| Integration | VS Code Extension (TypeScript) |
| CLI Tool | Python with click library |

---

## Learning Goals

- Instruction tuning with LoRA/QLoRA
- Dataset preparation for code generation
- Model quantization for local inference
- VS Code extension development
- AST manipulation in Python
- Code transformation pipelines

---

## Build Milestones

| Phase | Deliverable | Timeline |
|-------|-------------|----------|
| 1. Dataset | Collect and format training data | Week 1-2 |
| 2. Fine-Tuning | QLoRA fine-tune on Qwen2.5 | Week 3 |
| 3. Evaluation | Compare with base model | Week 4 |
| 4. CLI Tool | Command-line docstring generator | Week 5 |
| 5. VS Code | Extension with inline generation | Week 6 |
| 6. Styles | Support NumPy, Google, Sphinx formats | Week 7 |

---

## Reference Resources

- [Hugging Face PEFT Documentation](https://huggingface.co/docs/peft)
- [QLoRA Paper](https://arxiv.org/abs/2305.14314)
- [CodeLlama/Qwen2.5-Coder](https://huggingface.co/models?search=qwen2.5-coder)
- [VS Code Extension Guide](https://code.visualstudio.com/api/get-started/your-first-extension)
