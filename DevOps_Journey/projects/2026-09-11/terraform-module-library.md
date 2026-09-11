# Terraform 模块化基础设施模板库

## 概述
创建一套可复用的 Terraform 模块，覆盖 AWS/Azure/GCP 常见基础设施模式。

## 架构/结构
```
┌─────────────────────────────────────────────────────────┐
│              Terraform Module Library                     │
├──────────────┬──────────────┬──────────────┬────────────┤
│  Compute     │  Networking  │  Storage     │  Database  │
├──────────────┼──────────────┼──────────────┼────────────┤
│ • EC2 集群   │ • VPC 模板   │ • S3 存储    │ • RDS 模板 │
│ • ECS 服务   │ • 子网规划   │ • EBS 卷     │ • DynamoDB │
│ • EKS 集群   │ • NACL 规则  │ • Glacier    │ • ElastiCache│
│ • Lambda     │ • 负载均衡   │ • Backup     │ • DocumentDB│
└──────────────┴──────────────┴──────────────┴────────────┘
```

## 工作流
1. 定义模块接口（input/output）
2. 实现模块内部资源
3. 编写测试和文档
4. 发布到 Terraform Registry

## 工具
- Terraform
- Terratest（测试）
- Markdown（文档）
- GitHub Actions（CI）

## 学习目标
- Infrastructure as Code 最佳实践
- 模块设计与复用
- 多云策略
- 模块化 Terraform

## 构建里程碑
- [ ] 周 1：VPC 网络模块
- [ ] 周 2：EC2/ECS 计算模块
- [ ] 周 3：存储模块
- [ ] 周 4：数据库模块
- [ ] 周 5：测试框架与文档
