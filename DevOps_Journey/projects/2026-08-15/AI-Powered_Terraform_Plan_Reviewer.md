# AI-Powered Terraform Plan Reviewer

**Category:** Combined
**Suggested Date:** 2026-08-15
**Status:** Idea / Not Started

## Overview
A combined DevOps+AI tool that parses Terraform plan output, identifies risky changes (public IPs, over-permissioned IAM, large instance upgrades), and summarizes them as a readable AI-generated review before merge.

## What It Will Do
- Solve a practical problem related to combined.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
tf-plan-reviewer/
├── README.md
├── tf_parser/
│   ├── plan_reader.py
│   └── risk_classifier.py
├── llm_reviewer/
│   └── summarizer.py
├── policies/
├── github_app/
├── tests/
│   └── samples/
└── .github/workflows/

## How It Will Work
1. Define the core use case and minimal working workflow.
2. Build the API/automation pipeline first.
3. Add persistence, observability, and error handling.
4. Containerize the application and add CI.
5. Write documentation and create a demo scenario.

## Tools / Tech Stack
Terraform, GitHub Actions, OPA/Conftest, local LLM (Ollama/llama.cpp), Python, LangChain, FastAPI, Terraform plan JSON parser

## Learning Goals
Learn Terraform internals, plan parsing, risk classification, policy-as-code gates, AI-powered code review, and CI/CD integration patterns.

## Build Milestones
- **MVP:** Parse a sample Terraform plan JSON and highlight high-risk resources.
- **v1:** Integrate with GitHub PR comments using an LLM to summarize findings.
- **v2:** Add OPA policy gate that blocks merges on critical risks.
- **Portfolio polish:** Sample plan/review diff, policy library, deployment guide.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
