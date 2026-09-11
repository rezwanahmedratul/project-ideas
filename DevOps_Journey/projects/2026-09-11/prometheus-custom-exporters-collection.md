# Prometheus 自定义Exporter 集合

## 概述
为各种自研服务和内部工具开发 Prometheus Exporter，使其监控指标可被采集。

## 架构/结构
```
┌─────────────────────────────────────────────────────────┐
│              Custom Prometheus Exporters                 │
├──────────────┬──────────────┬──────────────┬────────────┤
│  Database    │  Application │  Infrastructure│  Custom  │
│  Exporter    │  Exporter    │  Exporter    │  Exporter  │
├──────────────┼──────────────┼──────────────┼────────────┤
│ • MySQL      │ • API 延迟   │ • 磁盘使用   │ • 业务指标 │
│ • PostgreSQL │ • 队列深度   │ • 网络流量   │ • 用户行为 │
│ • Redis      │ • 缓存命中   │ • CPU 温度   │ • 交易统计 │
│ • MongoDB    │ • 错误率     │ • 内存压力   │ • 自定义   │
└──────────────┴──────────────┴──────────────┴────────────┘
```

## 工作流
1. 定义需要暴露的指标
2. 实现 HTTP endpoint 暴露 metrics
3. 注册到 Prometheus  scrape 配置
4. Grafana 创建对应仪表板

## 工具
- Python + prometheus_client
- Go + prometheus/client_golang
- Node.js + prom-client
- Prometheus + Grafana

## 学习目标
- 监控指标设计规范
- HTTP metrics endpoint
- Prometheus 配置管理
- 仪表板设计

## 构建里程碑
- [ ] 周 1：Python Exporter 基础
- [ ] 周 2：Go Exporter 高性能版
- [ ] 周 3：数据库指标导出
- [ ] 周 4：自定义业务指标
- [ ] 周 5：统一管理与文档
