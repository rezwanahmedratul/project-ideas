# Project: Fine-Tuned Python Docstring Generator

**Category:** AI/ML  
**Date:** 2026-08-20

---

## Overview

Fine-tune an open-source LLM to generate consistent, high-quality docstrings for Python code following Google or NumPy style guides. Train on your codebase to match your team's documentation conventions.

---

## What It Does

- Analyze Python functions/classes and generate appropriate docstrings
- Follow selected style guide (Google, NumPy, Sphinx)
- Learn your team's conventions from existing documentation
- Integrate with pre-commit hooks for automatic generation
- Support for type hints and parameter descriptions

---

## Architecture/Structure

```
docstring-generator/
├── data/
│   └── training/         # Labeled function-docstring pairs
│       ├── examples.jsonl
│       └── validation.jsonl
├── src/
│   ├── trainer.py        # Fine-tuning script
│   ├── generator.py      # Inference pipeline
│   └── formatters.py     # Style guide formatters
├── scripts/
│   ├── preprocess.py     # Dataset preparation
│   └── pre_commit_hook.sh
├── fine_tuned_model/     # Trained model output
└── pyproject.toml
```

---

## Workflow

1. **Dataset creation:** Extract existing docstrings from codebase
2. **Preprocessing:** Format into training pairs (code → docstring)
3. **Fine-tuning:** LoRA/QLoRA on base model (Phi-3, Llama-3.2)
4. **Validation:** Test on held-out functions
5. **Integration:** Pre-commit hook runs on staged files
6. **Generation:** Appends missing docstrings or updates existing

---

## Tools/Tech Stack

| Component | Technology |
|-----------|------------|
| Base Model | Phi-3-mini, Llama-3.2-3B |
| Fine-tuning | Hugging Face Transformers, PEFT (LoRA) |
| Quantization | bitsandbytes (QLoRA) |
| Dataset | JSONL format, custom parser |
| Hook | pre-commit framework |
| Testing | pytest, coverage |

---

## Learning Goals

- Dataset curation and preprocessing for fine-tuning
- LoRA/QLoRA fine-tuning techniques
- Prompt formatting for code generation
- Pre-commit hook integration
- Evaluation metrics for generated documentation

---

## Build Milestones

1. **Week 1:** Dataset extraction from sample codebase
2. **Week 2:** Data preprocessing and cleaning
3. **Week 3:** Initial fine-tuning run
4. **Week 4:** Hyperparameter tuning and evaluation
5. **Week 5:** Pre-commit hook integration
6. **Week 6:** Style guide customization and docs

---

## Stretch Goals

- Multi-style support (switch between Google/NumPy/Sphinx)
- Inline comment to docstring conversion
- Team-specific convention learning
- VS Code extension for inline generation
