# Kubernetes 服务网格可观测性面板

**日期**: 2026-09-01  
**类别**: DevOps  
**难度**: 中级  
**预计工期**: 2-3周

---

## 概述

构建一个基于 Kubernetes Service Mesh（Istio/Linkerd）的可观测性仪表盘，实时可视化服务间调用链、延迟分布和错误率。集成 Prometheus + Grafana + Jaeger 实现全链路追踪。

---

## 架构结构

```
┌─────────────────────────────────────────────────────┐
│              可观测性面板 (React/Next.js)            │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐         │
│  │ 调用链   │  │ 指标     │  │ 告警     │         │
│  │ 图谱     │  │ 仪表板   │  │ 中心     │         │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘         │
└───────┼─────────────┼─────────────┼────────────────┘
        │             │             │
   ┌────▼────┐   ┌────▼────┐   ┌────▼────┐
   │ Jaeger  │   │Prometheus│   │Alertmanager│
   │ (追踪)  │   │  (指标) │   │  (告警)  │
   └────┬────┘   └────┬────┘   └────┬────┘
        │             │             │
   ┌────▼─────────────▼─────────────▼────┐
   │          Istio Sidecar               │
   │     (数据平面采集)                    │
   └──────────────────────────────────────┘
        │             │             │
   ┌────▼────┐   ┌────▼────┐   ┌────▼────┐
   │ServiceA │   │ServiceB │   │ServiceC │
   └─────────┘   └─────────┘   └─────────┘
```

---

## 工作流

1. **数据采集层**: Istio Envoy Sidecar 自动注入所有 Pod
2. **指标存储层**: Prometheus 每秒拉取 metrics
3. **追踪存储层**: Jaeger 接收分布式追踪span
4. **告警引擎**: Alertmanager 处理阈值告警
5. **可视化层**: Grafana 仪表板 + 自定义 React 面板

---

## 工具栈

- **编排**: Kubernetes 1.28+
- **Service Mesh**: Istio 1.20 / Linkerd 2.16
- **监控**: Prometheus + Grafana
- **追踪**: Jaeger
- **告警**: Alertmanager + PagerDuty webhook
- **前端**: React + D3.js + K6 图表库

---

## 学习目标

- 深入理解 Kubernetes Service Mesh 原理
- 掌握分布式追踪（Trace ID / Span ID）机制
- 学习 Prometheus 指标模型和 PromQL
- 实践 SLO/SLI 定义和告警策略

---

## 构建里程碑

| 阶段 | 任务 | 交付物 |
|------|------|--------|
| Week 1 | 部署 Istio + 示例应用 | 带 sidecar 的 K8s 集群 |
| Week 1 | 配置 Prometheus scraping | metrics endpoint 正常工作 |
| Week 2 | 部署 Jaeger + 集成追踪 | 调用链可视化 |
| Week 2 | Grafana 仪表板设计 | 核心指标面板 |
| Week 3 | 自定义 React 面板开发 | 服务拓扑图 |
| Week 3 | 告警规则配置 | Alertmanager 集成 |

---

**参考链接**: [Istio 官方文档](https://istio.io/latest/docs/), [Jaeger Tracing](https://www.jaegertracing.io/)
