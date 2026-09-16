# AI Software Dev Report #101 — RAG Systems & Vector Database Engineering

## Overview
Retrieval-Augmented Generation (RAG) has matured from a novel concept into an enterprise-standard architecture for deploying LLMs with proprietary or domain-specific knowledge. The ecosystem now includes specialized vector databases, hybrid search strategies, and automated evaluation pipelines.

## Core Architecture
1. **Ingestion Pipeline** — Document parsing, chunking strategies, embedding generation
2. **Vector Store** — Storage and indexing of high-dimensional embeddings
3. **Retrieval Layer** — Semantic search with reranking, hybrid text+vector queries
4. **Generation Layer** — LLM synthesis with retrieved context injected into prompts

## Vector Database Landscape (2025–2026)
| Platform | Type | Notable Features |
|----------|------|------------------|
| Pinecone | Cloud-native | Serverless, managed, 30x faster query speeds |
| Weaviate | Open-source + Cloud | Hybrid search, GraphQL API, module ecosystem |
| Milvus | Open-source | Multi-cluster, cross-cloud, Zilliz Cloud |
| pgvector | PostgreSQL extension | Relational + vector in one DB, simple deployment |
| Chroma | Local-first | Developer-friendly, embeddable |

## Key Research Findings
- **Chunk size** and **embedding model selection** are the two highest-impact parameters on RAG accuracy (MDPI 2025 study)
- **Hybrid architectures** combining dense vector retrieval + symbolic knowledge graphs are emerging as best practice
- On-premise/VPC-hosted vector databases address data privacy concerns for enterprise deployments

## Evaluation & Optimization
- Systematic methodologies now exist for measuring LLM+vector database tuning impact
- Supervised learning dominates; semi-supervised and unsupervised retrieval gaining traction for low-label scenarios
- Enterprise RAG + LLM research grew dramatically since 2020 with near-equal journal/conference publication split

## Reference Links
- [IBM — Vector Databases for RAG](https://www.ibm.com/think/topics/rag-vector-database)
- [DEV Community — Vector Databases Guide 2025](https://dev.to/klement_gunndu_e16216829c/vector-databases-guide-rag-applications-2025-55oj)
- [Systematic Review of RAG Systems (arXiv 2507.18910)](https://arxiv.org/html/2507.18910v1)
- [LLM Selection and Vector Database Tuning (MDPI 2025)](https://www.mdpi.com/2076-3417/15/20/10886)
- [Enterprise RAG + LLM Literature Review (MDPI 2025)](https://www.mdpi.com/2076-3417/16/1/368)
