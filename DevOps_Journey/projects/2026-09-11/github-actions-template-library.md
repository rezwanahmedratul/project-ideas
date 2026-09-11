# GitHub Actions 模块化模板库

## 概述
创建一套可复用的 GitHub Actions 工作流模板，覆盖常见 DevOps 场景。

## 架构/结构
```
┌─────────────────────────────────────────────────────────┐
│              GitHub Actions Template Library              │
├──────────────────┬──────────────────┬────────────────────┤
│  CI Templates    │  CD Templates    │  Utility Templates │
├──────────────────┼──────────────────┼────────────────────┤
│ • Build          │ • Deploy AWS     │ • Lint             │
│ • Test           │ • Deploy K8s     │ • Security Scan    │
│ • Docker Build   │ • Deploy Azure   │ • Version Bump     │
│ • Security Check │ • Notify         │ • Changelog        │
└──────────────────┴──────────────────┴────────────────────┘
```

## 工作流
1. 定义标准化模板结构
2. 使用 reusable workflows 实现复用
3. 提供参数化配置示例
4. 编写文档和使用指南

## 工具
- GitHub Actions
- YAML（工作流定义）
- Shell Script（脚本封装）
- Markdown（文档）

## 学习目标
- CI/CD 管道设计模式
- GitHub Actions 高级用法
- 模板化与参数化技巧
- DevOps 标准化实践

## 构建里程碑
- [ ] 周 1：CI 模板（构建+测试）
- [ ] 周 2：Docker 镜像构建模板
- [ ] 周 3：Kubernetes 部署模板
- [ ] 周 4：安全扫描模板
- [ ] 周 5：文档与示例项目
