# Fine-Tuned Python Docstring Generator

## Overview
A fine-tuned model that generates accurate, PEP 257-compliant docstrings for Python functions and classes from source code context.

## Architecture
```
┌─────────────────────────────────────────────┐
│          Python Source Code                 │
│  ┌─────────────────────────────────────┐    │
│  │ def process_data(df):               │    │
│  │     ...                             │    │
│  │                                     │    │
│  │ class DataProcessor:                │    │
│  │     ...                             │    │
│  └─────────────────────────────────────┘    │
└──────────────────────┬──────────────────────┘
                       │ AST Parse
                       ▼
          ┌────────────────────────┐
          │  Function/Class        │
          │  Signature Extractor   │
          └───────────┬────────────┘
                      │
          ┌───────────▼────────────┐
          │  Token Context Builder │
          │  (surrounding code)    │
          └───────────┬────────────┘
                      │
          ┌───────────▼────────────┐
          │  Fine-Tuned Model      │
          │  (Docstring format)    │
          └───────────┬────────────┘
                      │
          ┌───────────▼────────────┐
          │  Docstring Output      │
          │  (PEP 257 compliant)   │
          └────────────────────────┘
```

## Workflow
1. Scan Python file(s) for undocumented functions/classes
2. Extract signature and surrounding context
3. Generate docstring using fine-tuned model
4. Insert into source with proper formatting
5. Validate against PEP 257 conventions

## Training Approach
- **Base model**: CodeLlama or StarCoder
- **Training data**: Well-documented open-source Python projects
- **Format**: Google, NumPy, or Sphinx docstring styles
- **Fine-tuning method**: LoRA for efficiency

## Tools
- **Transformers** (Hugging Face) for model inference
- **LoRA/QLoRA** for parameter-efficient fine-tuning
- **Python ast module** for parsing
- **black** or **yapf** for formatting
- **pytest** for validation

## Learning Goals
- LLM fine-tuning workflows
- Document string standards (PEP 257)
- AST parsing and code analysis
- Evaluation metrics for generated documentation

## Build Milestones
1. [ ] Dataset collection and cleaning
2. [ ] Base model setup and inference
3. [ ] LoRA fine-tuning pipeline
4. [ ] Document string insertion tool
5. [ ] Format validation (PEP 257 checker)
6. [ ] IDE integration (VS Code extension)
7. [ ] Batch processing for entire repos
