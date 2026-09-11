# Rust 微服务框架模板

## 概述
使用 Rust 构建一个高性能微服务框架模板，包含服务发现、负载均衡、熔断等基础能力。

## 架构/结构
```
┌─────────────────────────────────────────────────────────┐
│                 Rust Microservice Framework               │
├──────────────────┬──────────────────┬────────────────────┤
│  Core Library    │  Service Traits  │  Middleware        │
├──────────────────┼──────────────────┼────────────────────┤
│ • HTTP Server    │ • Health Check   │ • Auth             │
│ • gRPC Support   │ • Metrics Export │ • Rate Limit       │
│ • Config Manager │ • Trace ID       │ • Retry            │
│ • Service Reg    │                  │ • Circuit Breaker  │
└──────────────────┴──────────────────┴────────────────────┘
```

## 工作流
1. 定义服务接口 trait
2. 实现框架核心组件
3. 提供脚手架工具生成新服务
4. 内置测试和基准测试

## 工具
- Rust + Tokio
- Hyper / Axum（HTTP）
- Prost（gRPC）
- Prometheus Client
- Cargo Workspaces

## 学习目标
- Rust 系统编程
- 微服务架构模式
- 异步编程模型
- 性能优化技巧

## 构建里程碑
- [ ] 周 1：项目结构与 HTTP 服务器
- [ ] 周 2：gRPC 集成
- [ ] 周 3：服务发现与注册
- [ ] 周 4：中间件链
- [ ] 周 5：文档与示例服务
