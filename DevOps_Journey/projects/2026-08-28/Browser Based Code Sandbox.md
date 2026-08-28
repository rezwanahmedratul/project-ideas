# Software Dev: Browser-Based Code Sandbox

## Overview
Build a web application that lets users write, execute, and share code snippets in multiple languages directly in the browser — with syntax highlighting, execution output, and collaborative editing. Think Judge0 meets CodePen.

## Architecture
```
Frontend (React/Vue) → API Gateway → Executor Service
                                             ├── Docker-based sandbox
                                             ├── Language runtimes (Node, Python, Rust, Go)
                                             └── Result store (Redis/PostgreSQL)
```

## Workflow
1. User writes code in browser editor
2. Sends to executor service with language specifier
3. Code runs in isolated Docker container with timeout/cap limits
4. Output/stderr captured and returned
5. Results displayed with syntax-colored output
6. Optionally saved to share via URL

## Tools
React, Node.js, Docker, Judge0 API or custom executor, Redis, PostgreSQL, WebSocket

## Learning Goals
- Secure code execution sandboxes
- WebSocket real-time collaboration
- Docker container lifecycle management
- Multi-language runtime orchestration

## Build Milestones
1. Basic single-language execution with Docker sandbox
2. Add syntax highlighting and output rendering
3. Implement multi-language support (Node, Python, Go)
4. Add WebSocket-based collaborative editing
5. Build sharing via permanent URLs with saved state
