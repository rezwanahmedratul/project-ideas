# Synthetic Test Data Generator

**Category:** AI / ML  
**Date:** 2026-08-19  
**Difficulty:** Intermediate  

## Overview
A tool that generates **realistic synthetic datasets** for testing ML pipelines and applications — tabular data with correlations, fake-but-plausible PII (names, addresses) that is safe to use, and labeled image/text augmentation. Tackles the 2026 theme that the best models are increasingly trained/evaluated on synthetic data. Useful for demos, load tests, and privacy-safe development.

## Architecture / Structure
```
synthest/
├── cli.py                # generate tabular / text / image
├── generators/
│   ├── tabular.py        # correlated columns via copulas/SDV
│   ├── pii.py            # Faker-based safe PII
│   └── text.py           # template + LLM augmentation
├── schemas/              # YAML dataset specs
├── eval.py               # distribution similarity checks
└── README.md
```

## Workflow
1. User defines a dataset spec (columns, types, correlations, volume).
2. Generator samples rows preserving specified distributions/correlations.
3. PII fields use Faker (clearly fake, no real persons).
4. Output written to CSV/Parquet/JSON; `eval.py` checks it matches the spec.
5. Optional: an LLM augments text fields for variety.

## Tools
- Python, `Faker`, `SDV` (synthetic data vault) or `copulas`
- `pandas` / `pyarrow` (Parquet)
- Optional: local LLM via `llama.cpp` for text augmentation
- `pytest` for spec validation

## Learning Goals
- Synthetic data generation techniques and when to use them.
- Preserving statistical properties (correlation, distributions).
- Privacy-safe data handling (no real PII).
- Validating generated data quality.

## Build Milestones
1. Build a tabular generator with typed columns + seeds.
2. Add correlated columns and distribution control.
3. Add Faker-based PII fields with a "safe/fake" guarantee.
4. Add an LLM-backed text augmenter (local model).
5. Write `eval.py` to assert generated data matches the spec.
