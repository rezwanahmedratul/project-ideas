# MCP Server for Homelab Operations

**日期**: 2026-09-01  
**类别**: Combined  
**难度**: 中级  
**预计工期**: 2-3周

---

## 概述

构建一个 Model Context Protocol (MCP) Server，让 Claude Code 等 AI 编程代理能够直接操作家庭实验室基础设施——查询 Proxmox VM 状态、管理 Docker 容器、查看监控系统指标。

---

## 架构结构

```
┌──────────────────────────────────────────────────────────────┐
│            MCP Server for Homelab                            │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌─────────────┐     ┌─────────────┐     ┌─────────────┐    │
│  │ Claude Code  │◄───│  MCP Server │◄───│  HomeLab    │    │
│  │ (Client)    │     │ (STDIO/HTTP)│     │  Resources  │    │
│  └─────────────┘     └──────┬──────┘     └──────┬──────┘    │
│                             │                   │            │
│                    ┌────────▼────────┐   ┌──────▼──────┐     │
│                    │ Tool Registry   │   │ Resource    │     │
│                    │ (Tools/Cases)   │   │ Adapters    │     │
│                    └─────────────────┘   └─────────────┘     │
└──────────────────────────────────────────────────────────────┘
```

---

## 支持的资源适配

### 1. Proxmox VE
```python
# MCP Tools
- proxmox.list_vms()         # 列出所有虚拟机
- proxmox.get_vm_status(vm_id)  # 获取 VM 状态
- proxmox.start_vm(vm_id)    # 启动虚拟机
- proxmox.shutdown_vm(vm_id) # 关机虚拟机
- proxmox.create_snapshot(vm_id, tag)  # 创建快照
- proxmox.get_vm_metrics(vm_id)       # 获取性能指标
```

### 2. Docker / Podman
```python
- docker.list_containers()          # 列出容器
- docker.get_container_logs(id)     # 获取容器日志
- docker.restart_container(id)      # 重启容器
- docker.execute_command(id, cmd)   # 在容器内执行命令
- docker.get_resource_usage()       # 资源使用情况
```

### 3. Monitoring Stack
```python
- prometheus.query(query)           # PromQL 查询
- grafana.get_dashboard(name)       # 获取仪表板
- alertmanager.get_alerts()         # 当前告警列表
```

### 4. 网络管理
```python
- network.get_dns_records()         # DNS 记录
- network.check_connectivity(host)  # 连通性检测
- network.get_bandwidth()           # 带宽使用
```

---

## 安全考虑

- **RBAC 权限**: 不同操作需要不同权限级别
- **操作确认**: 危险操作需要二次确认
- **审计日志**: 所有操作记录可追溯
- **命令白名单**: 限制可执行的 shell 命令

---

## 工具栈

- **MCP SDK**: @modelcontextprotocol/sdk (TypeScript)
- **Proxmox API**: proxmoxer (Python)
- **Docker SDK**: docker-py / podman-py
- **Prometheus**: prometheus-api-client
- **运行方式**: Node.js 进程，STDIO 通信

---

## 学习目标

- 理解 MCP 协议规范和实现
- 学习家庭实验室基础设施管理
- 掌握 AI Agent 与外部系统集成
- 实践安全的远程操作设计

---

## 构建里程碑

| 阶段 | 任务 | 交付物 |
|------|------|--------|
| Week 1 | MCP Server 骨架 | STDIO 通信框架 |
| Week 1 | Proxmox 适配 | VM 管理工具集 |
| Week 2 | Docker 适配 | 容器管理工具集 |
| Week 2 | 监控适配 | Prometheus/Grafana |
| Week 3 | 安全控制 | RBAC + 审计日志 |
| Week 3 | 集成测试 | Claude Code 调用验证 |

---

**参考链接**: [Model Context Protocol Docs](https://modelcontextprotocol.io/), [Proxmox VE API](https://pve.proxmox.com/wiki/Proxmox_VE_API), [MCP TypeScript SDK](https://github.com/modelcontextprotocol/typescript-sdk)
