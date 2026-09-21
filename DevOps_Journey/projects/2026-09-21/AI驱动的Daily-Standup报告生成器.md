# 综合项目 1：AI 驱动的 Daily Standup 报告生成器

**日期：** 2026-09-21  
**分类：** DevOps + AI / 自动化 / 个人效率

---

## 📋 概述
整合 Git commit 历史、Jira/线性工单和日历事件，使用 LLM 自动生成每日站会报告，支持 Slack/邮件发送。

## 🏗️ 架构设计
```
┌─────────────────────────────────────────────────────────────┐
│                   Daily Standup Pipeline                     │
│                                                              │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│  │ Git      │  │ Jira/    │  │ Calendar │  │ PR/      │   │
│  │ Commits  │  │ Linear   │  │ Events   │  │ Issues   │   │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘   │
│       │             │             │             │          │
│       └─────────────┴─────────────┴─────────────┘          │
│                            ↓                               │
│              ┌─────────────────────┐                       │
│              │  LLM Summarizer     │                       │
│              │  (GPT-4o / Claude)  │                       │
│              └──────────┬──────────┘                       │
│                         ↓                                  │
│              ┌─────────────────────┐                       │
│              │  Delivery Channel   │                       │
│              │  Slack / Email /    │                       │
│              │  WhatsApp Bot       │                       │
│              └─────────────────────┘                       │
└─────────────────────────────────────────────────────────────┘
```

## 🛠️ 技术栈
- **数据源：** Git CLI、Jira API、Google Calendar API
- **LLM：** GPT-4o-mini 或 Claude 3 Haiku
- **调度：** cron / GitHub Actions
- **消息推送：** Slack Webhook / SendGrid / Telegram Bot

## 📚 学习目标
- 多数据源聚合与时间线对齐
- LLM Prompt Engineering 最佳实践
- 自动化报告的个性化定制

## 🎯 构建里程碑
| 阶段 | 任务 | 预计时间 |
|------|------|----------|
| M1 | Git Commit 历史解析 | 2h |
| M2 | Jira/Linear API 对接 | 2h |
| M3 | LLM 报告生成 Prompt | 2h |
| M4 | 多渠道推送集成 | 2h |
| M5 | 定时调度与错误处理 | 2h |

**总工时：** 约 10 小时
