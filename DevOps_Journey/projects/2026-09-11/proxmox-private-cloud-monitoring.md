# Proxmox 私有云监控系统

## 概述
为家庭实验室的 Proxmox VE 集群构建完整的监控与告警系统。

## 架构/结构
```
┌─────────────────────────────────────────────────────┐
│                  Proxmox 集群                         │
├─────────────┬─────────────┬─────────────┬────────────┤
│ PVE Node 1  │ PVE Node 2  │ PVE Node 3  │ 存储节点   │
│ (VMs + CT)  │ (VMs + CT)  │ (VMs + CT)  │ (Ceph)    │
└──────┬──────┴──────┬──────┴──────┬──────┴─────┬─────┘
       │             │             │            │
       └─────────────┴─────────────┴────────────┘
                          │
                          ▼
              ┌───────────────────────┐
              │   Prometheus + Grafana │
              │   (监控采集 + 可视化)   │
              └───────────────────────┘
                          │
                          ▼
              ┌───────────────────────┐
              │   Alertmanager        │
              │   (告警路由 + 通知)     │
              └───────────────────────┘
```

## 工作流
1. node_exporter + proxmox_exporter 采集指标
2. Prometheus 持久化存储
3. Grafana 仪表板展示关键指标
4. Alertmanager 发送告警至 Telegram/WhatsApp

## 工具
- Proxmox VE
- Prometheus + Grafana
- node_exporter / proxmox_exporter
- Alertmanager
- Telegraf（可选）

## 学习目标
- 虚拟化技术基础
- 监控系统架构设计
- 指标采集与告警配置
- 仪表板可视化

## 构建里程碑
- [ ] 周 1：Proxmox 集群部署
- [ ] 周 2：Prometheus 数据采集
- [ ] 周 3：Grafana 仪表板
- [ ] 周 4：告警规则配置
- [ ] 周 5：Telegram/WhatsApp 集成
