# Small Model Fine-Tuning Playground

**Category:** AI ML
**Suggested Date:** 2026-08-15
**Status:** Idea / Not Started

## Overview
A hands-on lab for fine-tuning small open-source LLMs (7B parameters or less) on domain-specific datasets, with wandb tracking and side-by-side evaluation dashboards.

## What It Will Do
- Solve a practical problem related to ai ml.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
fine-tuning-playground/
├── README.md
├── notebooks/
│   ├── 01_baseline_eval.ipynb
│   ├── 02_lora_finetune.ipynb
│   └── 03_evaluation_dashboard.ipynb
├── scripts/
│   ├── train.sh
│   └── eval.sh
├── datasets/
├── models/
└── configs/

## How It Will Work
1. Define the core use case and minimal working workflow.
2. Build the API/automation pipeline first.
3. Add persistence, observability, and error handling.
4. Containerize the application and add CI.
5. Write documentation and create a demo scenario.

## Tools / Tech Stack
Hugging Face Transformers, PEFT/LoRA, QLoRA, vLLM or Ollama for serving, W&B or MLflow, Python, Jupyter, fast.ai or custom training loops

## Learning Goals
Learn transfer learning, parameter-efficient fine-tuning, LoRA/QLoRA techniques, GPU memory optimization, evaluation methodologies, and model deployment.

## Build Milestones
- **MVP:** Fine-tune a 7B model on a single-shot custom dataset.
- **v1:** Add LoRA adapters, wandb tracking, and BLEU/accuracy eval.
- **v2:** Multi-dataset comparison dashboard with AB test framework.
- **Portfolio polish:** Training run report, cost analysis, reproducible notebooks.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
