# AI/ML: Multimodal Search Engine

## Overview
Build a search engine that indexes documents, images, and code snippets, allowing users to search across all modalities using either text queries or image uploads — powered by CLIP embeddings and vector search.

## Architecture
```
Indexer (background)
   ├── Text Pipeline: tokenizer → embedding → ChromaDB
   ├── Image Pipeline: CLIP → embedding → ChromaDB
   └── Code Pipeline: code embeddings → ChromaDB
                ↓
        Query Router
   ├── Text query → embedding → hybrid search (BM25 + vector)
   ├── Image upload → CLIP encode → nearest neighbor lookup
   └── Code query → code embedding → similarity search
                ↓
           Results Ranker
```

## Workflow
1. Crawl/index a collection of markdown docs, images, and code repos
2. Generate embeddings using CLIP (images) and text-embedding-3 (text/code)
3. Store in ChromaDB with source metadata
4. At query time, match against both text and visual similarities
5. Return ranked results with modality tags

## Tools
Python, CLIP (OpenAI), sentence-transformers, ChromaDB, FastAPI, React frontend

## Learning Goals
- Multimodal embedding models (CLIP)
- Hybrid search (keyword + vector)
- Embedding management at scale
- Cross-modal retrieval techniques

## Build Milestones
1. Build document and image indexer with CLIP embeddings
2. Implement ChromaDB storage with metadata filtering
3. Create text-based search with BM25 + vector hybrid
4. Add image-to-text and image-to-image search
5. Build React frontend with query suggestions and result preview
