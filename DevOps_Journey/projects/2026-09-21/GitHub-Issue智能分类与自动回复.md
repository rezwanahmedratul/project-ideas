# AI/ML 项目 3：GitHub Issue 智能分类与自动回复

**日期：** 2026-09-21  
**分类：** AI/ML / NLP / GitHub Integration

---

## 📋 概述
构建一个 GitHub App，自动对 Issue 和 PR 进行分类、标签分配，并在合适时生成回复建议，减轻维护者负担。

## 🏗️ 架构设计
```
┌─────────────────────────────────────────────────────────────┐
│                    GitHub Webhook Receiver                  │
│                     (Cloud Functions / VPS)                  │
└─────────────────────────────────────────────────────────────┘
                              ↓
        ┌─────────────────────┼─────────────────────┐
        ↓                     ↓                     ↓
   ┌──────────┐          ┌──────────┐          ┌──────────┐
   │ Classify │          │ Label    │          │ Reply    │
   │ Issue    │          │ Assign   │          │ Suggest  │
   └────┬─────┘          └────┬─────┘          └────┬─────┘
        │                     │                     │
        └─────────────────────┼─────────────────────┘
                              ↓
                    ┌─────────────────┐
                    │  LLM (GPT-3.5   │
                    │  / Claude Haiku) │
                    └─────────────────┘
```

## 🛠️ 技术栈
- **GitHub API：** PyGithub / GitHub REST API
- **LLM：** OpenAI GPT-3.5-Turbo 或 Claude Haiku
- **部署：** GitHub Actions / Cloud Functions
- **缓存：** Redis (去重与状态跟踪)

## 📚 学习目标
- 掌握 GitHub Webhook 事件处理
- 学习文本分类模型微调（Few-shot Prompting）
- 理解自动化工作流的最佳实践

## 🎯 构建里程碑
| 阶段 | 任务 | 预计时间 |
|------|------|----------|
| M1 | GitHub App 基础框架 | 2h |
| M2 | Issue 文本提取与预处理 | 2h |
| M3 | LLM 分类 Prompt 设计 | 2h |
| M4 | 自动标签与回复建议 | 3h |
| M5 | 部署到 GitHub Marketplace | 2h |

**总工时：** 约 11 小时
