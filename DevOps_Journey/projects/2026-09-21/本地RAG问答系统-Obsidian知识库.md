# AI/ML 项目 1：本地 RAG 问答系统（Obsidian 知识库）

**日期：** 2026-09-21  
**分类：** AI/ML / RAG / LangChain

---

## 📋 概述
构建一个基于本地 Obsidian 知识库的 RAG 问答系统，使用 Ollama 运行本地 LLM，实现隐私保护的个人知识检索。

## 🏗️ 架构设计
```
┌─────────────────────────────────────────────────────────────┐
│                    Query Interface                           │
│  "我的 K8s 项目遇到了什么问题？"                             │
└─────────────────────────────────────────────────────────────┘
                              ↓
        ┌─────────────────────┼─────────────────────┐
        ↓                     ↓                     ↓
   ┌──────────┐          ┌──────────┐          ┌──────────┐
   │ Embedding │          │  LLM     │          │  Response│
   │ Model     │          │ (Llama   │          │  Generator│
   │ (BGE)    │          │  3 8B)   │          │          │
   └────┬─────┘          └──────────┘          └──────────┘
        │
        ↓
   ┌─────────────────────────────────────┐
   │        Vector Database              │
   │      (ChromaDB / LanceDB)           │
   │   ┌─────────┐ ┌─────────┐          │
   │   │ Obsidian│ │ Projects│          │
   │   │ Notes   │ │ Docs    │          │
   │   └─────────┘ └─────────┘          │
   └─────────────────────────────────────┘
```

## 🛠️ 技术栈
- **LLM：** Ollama (Llama-3.1-8B / Qwen2.5-7B)
- **Embedding：** BGE-M3 或 nomic-embed-text
- **向量库：** ChromaDB (轻量) 或 LanceDB
- **框架：** LangChain / LlamaIndex
- **接口：** Gradio / Streamlit Web UI

## 📚 学习目标
- 理解 RAG（检索增强生成）完整流程
- 掌握 Embedding 模型选型与优化
- 学习 LangChain Chain 与 Agent 设计

## 🎯 构建里程碑
| 阶段 | 任务 | 预计时间 |
|------|------|----------|
| M1 | Obsidian 文档导入与分块 | 2h |
| M2 | Embedding 模型部署与测试 | 2h |
| M3 | 向量库搭建与索引 | 2h |
| M4 | RAG Pipeline 联调 | 3h |
| M5 | Web UI 开发与优化 | 3h |

**总工时：** 约 12 小时
