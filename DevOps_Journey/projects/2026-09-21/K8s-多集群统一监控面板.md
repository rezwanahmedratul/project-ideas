# DevOps 项目 1：K8s 多集群统一监控面板

**日期：** 2026-09-21  
**分类：** DevOps / Kubernetes / 可观测性

---

## 📋 概述
构建一个跨多个 Kubernetes 集群的统一监控 Dashboard，集成 Prometheus + Grafana + Alertmanager，实现对生产、预发、开发环境的集中可视化管理。

## 🏗️ 架构设计
```
┌─────────────────────────────────────────────────────────────┐
│                    Grafana Dashboard                        │
│              (统一视图 / 多集群切换)                          │
└─────────────────────────────────────────────────────────────┘
                              ↑
        ┌─────────────────────┼─────────────────────┐
        ↓                     ↓                     ↓
   ┌──────────┐          ┌──────────┐          ┌──────────┐
   │ Cluster A │          │ Cluster B │          │ Cluster C │
   │ (生产)    │          │ (预发)    │          │ (开发)    │
   └────┬─────┘          └────┬─────┘          └────┬─────┘
        │                     │                     │
   Prometheus                Prometheus           Prometheus
        │                     │                     │
   kube-state-metrics     kube-state-metrics    kube-state-metrics
```

## 🛠️ 技术栈
- **编排：** Helm + Kustomize
- **监控：** Prometheus + Node Exporter + kube-state-metrics
- **可视化：** Grafana (自建或云原生 GKE/AKS/EKS)
- **告警：** Alertmanager + Webhook → Telegram/WhatsApp Bot
- **配置管理：** GitOps (ArgoCD/Flux)

## 📚 学习目标
- 理解多集群 Prometheus 远程读写（Remote Read/Write）
- 掌握 Grafana Dashboard 模板化与变量查询
- 学习 Alertmanager 路由规则与分级告警

## 🎯 构建里程碑
| 阶段 | 任务 | 预计时间 |
|------|------|----------|
| M1 | 单集群部署 Prometheus + Grafana | 2h |
| M2 | 多集群 Federated Scrape 配置 | 3h |
| M3 | Grafana 统一 Dashboard 搭建 | 2h |
| M4 | Alertmanager 告警路由测试 | 2h |
| M5 | GitOps 自动化部署流程 | 3h |

**总工时：** 约 12 小时
