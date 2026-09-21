# DevOps 项目 3：Ansible 自动化配置工厂

**日期：** 2026-09-21  
**分类：** DevOps / 配置管理 / Ansible

---

## 📋 概述
构建基于 Ansible 的配置管理工厂，支持从基础设施初始化到应用部署的全自动化流水线，适用于 NixOS 与非 NixOS 混合环境。

## 🏗️ 架构设计
```
┌─────────────────────────────────────────────────────────────┐
│                    Ansible Control Node                      │
│                 (GitLab Runner / CI 节点)                    │
└─────────────────────────────────────────────────────────────┘
                              │
        ┌─────────────────────┼─────────────────────┐
        ↓                     ↓                     ↓
   ┌──────────┐          ┌──────────┐          ┌──────────┐
   │ Linux    │          │ macOS    │          │ WSL/     │
   │ Server   │          │ Dev      │          │ Windows  │
   └──────────┘          └──────────┘          └──────────┘
```

## 🛠️ 技术栈
- **配置管理：** Ansible ≥ 2.15
- **动态 Inventory：** ansible-inventory 或 AWX/Ansible Tower
- **密码管理：** Ansible Vault + HashiCorp Vault
- **测试：** Molecule + pytest
- **可视化：** Ansible Automation Controller 或 AWX

## 📚 学习目标
- 掌握 Ansible Role 与 Collection 的最佳实践
- 学习 Dynamic Inventory 对接云平台 API
- 理解 Ansible Vault 密钥轮换策略

## 🎯 构建里程碑
| 阶段 | 任务 | 预计时间 |
|------|------|----------|
| M1 | 基础 Role 开发（用户/SSH/安全加固） | 2h |
| M2 | 应用部署 Role（Docker/Nginx/Postgres） | 3h |
| M3 | Dynamic Inventory 脚本编写 | 2h |
| M4 | Molecule 测试框架集成 | 2h |
| M5 | AWX/Webhook 自动化触发 | 3h |

**总工时：** 约 12 小时
