# Competitive Programming Platform with AI Judge & Mentor

**Date:** 2026-08-27
**Category:** Software Development
**Tags:** competitive-programming, judge, ai, typescript, docker

---

## Overview

Build a competitive programming platform where users solve algorithmic problems, submit code, and receive AI-powered hints and explanations. The system includes a sandboxed judge, problem library, ranking system, and intelligent mentor features.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Frontend (React)                        │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────────┐  │
│  │ Problem  │ │ Coding   │ │ Stats    │ │ Discussion   │  │
│  │ Browser  │ │ Arena    │ │ Dashboard│ │ Forum        │  │
│  └──────────┘ └──────────┘ └──────────┘ └──────────────┘  │
└─────────────────────────────────────────────────────────────┘
                          │
                          ▼ HTTPS/WebSocket
┌─────────────────────────────────────────────────────────────┐
│                     Backend (Node.js)                       │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────────┐  │
│  │ Auth     │ │ Problem  │ │ Judge    │ │ AI Mentor    │  │
│  │ Service  │ │ Service  │ │ Service  │ │ Service      │  │
│  └──────────┘ └──────────┘ └──────────┘ └──────────────┘  │
└─────────────────────────────────────────────────────────────┘
                          │
              ┌───────────┴───────────┐
              ▼                       ▼
┌─────────────────────┐    ┌─────────────────────┐
│  Judge Containers   │    │  Redis + PostgreSQL │
│  (Docker/sandbox)   │    │  (Cache + DB)       │
└─────────────────────┘    └─────────────────────┘
```

## Core Components

### Problem Library
- Problem statements with examples and constraints
- Difficulty rating (Easy/Medium/Hard) based on historical solve rates
- Tags: Dynamic Programming, Graph Theory, Greedy, etc.
- Test cases: hidden + sample, stored securely

### Judge Service
- Each submission runs in isolated Docker container
- Time/memory limits enforced by cgroups
- Output captured and compared against expected
- Languages supported: Python, JavaScript, C++, Rust

### AI Mentor
- Analyzes user's incorrect submissions
- Provides hints without giving away full solution
- Identifies algorithmic pattern needed
- Explains time/space complexity of optimal solution

### Ranking System
- ELO-based rating per problem category
- Global leaderboard
- Contest scheduling and scoring

## Technology Stack

| Component | Technology |
|-----------|------------|
| Frontend | React + TypeScript + Monaco Editor |
| Backend | Node.js + Express + WebSocket |
| Database | PostgreSQL (problems, users) + Redis (cache/jobs) |
| Judge | Docker containers with seccomp profiles |
| AI | OpenAI API or local LLM for hints |
| Storage | S3-compatible for test cases, submissions |

## Learning Goals

- Building a secure code execution sandbox
- WebSocket real-time features (live standings)
- Problem difficulty modeling
- AI prompt engineering for educational hints
- Contest scheduling and scoring algorithms

## Build Milestones

1. [ ] Database schema for users, problems, submissions
2. [ ] Judge container infrastructure with resource limits
3. [ ] Problem CRUD and test case management
4. [ ] Submission endpoint with async processing queue
5. [ ] Frontend coding arena with Monaco editor
6. [ ] AI mentor integration for hint generation
7. [ ] Leaderboard and rating system
8. [ ] Live contest mode with real-time updates

---
*Generated: 2026-08-27*
