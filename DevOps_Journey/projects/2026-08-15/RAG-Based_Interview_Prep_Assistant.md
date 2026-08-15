# RAG-Based Interview Prep Assistant

**Category:** AI ML
**Suggested Date:** 2026-08-15
**Status:** Idea / Not Started

## Overview
A personal interview preparation tool that indexes a user's resume, project notes, and learning journal, then generates tailored technical questions and evaluates responses with feedback.

## What It Will Do
- Solve a practical problem related to ai ml.
- Produce a working, portfolio-ready project you can deploy or demo.
- Teach production-style design rather than only tutorial-level implementation.

## Structure / Architecture
rag-interview-prep/
├── README.md
├── ingestion/
│   ├── resume_parser.py
│   └── note_loader.py
├── rag/
│   ├── retriever.py
│   └── generator.py
├── evaluator/
├── api/
├── ui/
└── data/
    └── knowledge_base/

## How It Will Work
1. Define the core use case and minimal working workflow.
2. Build the API/automation pipeline first.
3. Add persistence, observability, and error handling.
4. Containerize the application and add CI.
5. Write documentation and create a demo scenario.

## Tools / Tech Stack
Ollama or llama.cpp, ChromaDB or Qdrant, LangChain/LlamaIndex, sentence-transformers, FastAPI, React chat UI, Obsidian markdown integration

## Learning Goals
Learn RAG pipelines, vector embeddings, prompt engineering, contextual retrieval, conversational UI design, and personalized AI interaction patterns.

## Build Milestones
- **MVP:** Query your own notes with simple RAG and get related facts back.
- **v1:** Generate interview questions from indexed material.
- **v2:** Evaluate answer quality against ideal responses with rubric scoring.
- **Portfolio polish:** Evaluation dataset, response quality metrics, demo video.

## Notes
Keep this project small at first, then expand with real-world features after the MVP works.
