# Project: Real-time Chat Application with RAG and Context Memory

## Overview
Build a web-based chat application where conversations persist across sessions and the AI assistant can reference previous messages using vector embeddings and retrieval-augmented generation (RAG).

## Architecture
```
User → Chat Interface → API Server → LLM + Context → Response
              ↓              ↓            ↓
        WebSocket    PostgreSQL     Embedding Store
                                  (PGVector/Chroma)
```

## Workflow
1. User opens chat session (unique ID)
2. Messages stored in PostgreSQL with timestamps
3. On each new message:
   - Retrieve relevant conversation history (last N messages)
   - Retrieve relevant past contexts via vector search
   - Construct prompt with conversation + context
   - Call LLM (Claude/GPT) for response
4. Store response and update embeddings
5. Render in real-time via WebSocket

## Tools
- **React** or **Vue.js** for frontend
- **FastAPI** or **Express** for backend
- **PostgreSQL** + **pgvector** for message storage
- **ChromaDB** or **Pinecone** for vector embeddings
- **OpenAI/Claude API** for LLM

## Learning Goals
- Real-time communication with WebSockets
- Vector databases and similarity search
- RAG implementation patterns
- Conversation state management

## Build Milestones
- [ ] Week 1: Basic chat UI and message storage
- [ ] Week 2: WebSocket integration for real-time updates
- [ ] Week 3: Vector embedding and retrieval system
- [ ] Week 4: LLM integration with context assembly
- [ ] Week 5: Session persistence and conversation history

## Estimated Time
3-4 weeks (part-time)

## Difficulty
Intermediate — modern full-stack project with AI integration
