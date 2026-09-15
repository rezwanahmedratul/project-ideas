# Production RAG Infrastructure with Vector Databases

**Category:** Combined  
**Date:** 2026-09-15  
**Tags:** rag, vector-database, production, llm, embeddings

---

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    End Users                                │
│              (Question: "How do I configure...?")           │
└─────────────────────────────┬───────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│              Query Processing                               │
│  ┌─────────────┐  ┌─────────────┐  ┌──────────────────┐   │
│  │  Query      │  │  Cache      │  │  Reranking       │   │
│  │  Encoder    │  │  (Redis)    │  │  Service         │   │
│  └─────────────┘  └─────────────┘  └──────────────────┘   │
└─────────────────────────────┬───────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│              Vector Database Cluster                        │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  Primary  │  Replica  │  Replica                      │   │
│  │  (Pgvector│  │ (Pgvector│  │ (Pgvector                │   │
│  │   shard 1)│   │  shard 2)│  │  shard 3)               │   │
│  └─────────────────────────────────────────────────────┘   │
│  • Hybrid search (vector + metadata filters)               │
│  • Automatic failover                                      │
│  • Horizontal scaling                                      │
└─────────────────────────────┬───────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│              LLM Response Generation                        │
│  ┌─────────────┐  ┌─────────────┐  ┌──────────────────┐   │
│  │  Context    │  │  LLM        │  │  Response        │   │
│  │  Assembly   │  │  (Claude/   │  │  Validator       │   │
│  │             │  │   GPT)      │  │  (Hallucination  │   │
│  └─────────────┘  └─────────────┘  │  detection)      │   │
│                                   └──────────────────┘   │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                   Output                                    │
│              + Source citations                             │
│              + Confidence score                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Key Components

### 1. Document Ingestion Pipeline
```python
# ingestion.py
from langchain.document_loaders import DirectoryLoader
from langchain.text_splitter import RecursiveCharacterTextSplitter
from langchain.embeddings import FastEmbedEmbeddings
import psycopg2

class DocumentPipeline:
    def __init__(self):
        self.embeddings = FastEmbedEmbeddings()
        self.splitter = RecursiveCharacterTextSplitter(
            chunk_size=1000,
            chunk_overlap=200
        )
    
    def ingest(self, directory: str):
        loader = DirectoryLoader(directory)
        documents = loader.load()
        
        # Split into chunks
        chunks = self.splitter.split_documents(documents)
        
        # Generate embeddings
        for chunk in chunks:
            embedding = self.embeddings.embed_query(chunk.page_content)
            self.store_chunk(chunk, embedding)
        
        return len(chunks)
    
    def store_chunk(self, chunk, embedding: list):
        # Store in PostgreSQL with pgvector
        conn = psycopg2.connect(DB_URL)
        cur = conn.cursor()
        cur.execute("""
            INSERT INTO chunks (content, embedding, metadata, source)
            VALUES (%s, %s, %s, %s)
        """, (chunk.page_content, embedding, chunk.metadata, chunk.metadata.get('source')))
        conn.commit()
```

### 2. Hybrid Search
```python
# search.py
class HybridSearch:
    def search(self, query: str, filters: dict = None, top_k: int = 10):
        # Get query embedding
        query_embedding = self.embeddings.embed_query(query)
        
        # Vector similarity search
        vector_results = self.vector_search(query_embedding, top_k=top_k * 2)
        
        # Keyword search (for metadata filtering)
        keyword_results = self.keyword_search(query, filters)
        
        # Combine and rerank
        combined = self.combine_results(vector_results, keyword_results)
        reranked = self.reranker.rerank(combined, query)
        
        return reranked[:top_k]
```

### 3. Reranking Service
```python
# reranker.py
from cross_encoder import CrossEncoder

class Reranker:
    def __init__(self):
        self.model = CrossEncoder('cross-encoder/ms-marco-MiniLM-L-6-v2')
    
    def rerank(self, documents: List[Document], query: str) -> List[Document]:
        pairs = [[query, doc.content] for doc in documents]
        scores = self.model.predict(pairs)
        
        # Sort by relevance score
        for doc, score in zip(documents, scores):
            doc.relevance_score = float(score)
        
        return sorted(documents, key=lambda x: x.relevance_score, reverse=True)
```

---

## Production Considerations

### Caching Strategy
| Layer | Technology | Purpose |
|-------|------------|---------|
| Query cache | Redis | Cache frequent queries |
| Embedding cache | Local | Avoid regenerating embeddings |
| Response cache | Redis | Cache LLM responses for identical queries |

### Scaling Patterns
- **Read scaling**: Add read replicas for vector database
- **Write scaling**: Batch ingestion jobs with backpressure
- **Compute scaling**: Horizontal pod autoscaling for inference

### Monitoring Metrics
- Query latency (p50, p95, p99)
- Retrieval accuracy (hit rate at top-k)
- LLM token usage and cost
- Cache hit rate

---

## Tools

| Tool | Purpose |
|------|---------|
| **PostgreSQL + pgvector** | Vector database |
| **Milvus/Pinecone** | Alternative vector DB |
| **FastEmbed** | Embedding generation |
| **Cross-Encoder** | Reranking |
| **Redis** | Caching |
| **LangChain** | Orchestration |
| **Prometheus/Grafana** | Monitoring |

---

## Learning Goals

- [ ] Vector database fundamentals
- [ ] Embedding generation at scale
- [ ] RAG optimization techniques
- [ ] Production monitoring and alerting
- [ ] Hybrid search implementation

---

## Build Milestones

| Phase | Description | Estimated Time |
|-------|-------------|----------------|
| 1 | Set up vector database | 2 days |
| 2 | Build document ingestion pipeline | 3 days |
| 3 | Implement similarity search | 2 days |
| 4 | Add reranking service | 2 days |
| 5 | Create monitoring dashboard | 2 days |
| 6 | Load test and optimize | 3 days |

**Total: ~14 days**

---

## Success Criteria

- [ ] Sub-second response times for 95% of queries
- [ ] Top-3 retrieval accuracy > 85%
- [ ] Handles 1000+ concurrent queries
- [ ] Supports incremental document updates
- [ ] Clear source attribution in responses

---

*Reference: LangChain Documentation, Pgvector Documentation*
