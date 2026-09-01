# AI Software Development Report #62: SWE-bench Pro 与新编程评估范式

**日期**: 2026-09-01  
**类别**: AI Software Development  
**关键词**: SWE-bench Pro、ProgramBench、代码生成评估、Agent基准

---

## 核心趋势

2026年是软件工程师基准测试的关键年份。SWE-bench Pro 和 ProgramBench 的推出，标志着 AI 编程评估从"代码片段正确性"向"完整软件工程能力"转变。

---

## 重点进展

### 1. SWE-bench Pro 排行榜 (2026年9月)

SWE-bench Pro 是一个长周期仓库级基准测试，测试 AI 模型解决实际软件工程问题的能力：

| 模型 | SWE-bench Pro 得分 |
|------|-------------------|
| Claude Mythos 5 | 80.3% |
| GPT-5.6 Luna | 76.8% |
| Claude Fable 5 | 74.2% |
| Gemini 2.5 Pro | 71.5% |
| DeepSeek V3.5 | 68.9% |

> 来源: [BenchLM - SWE-bench Pro Leaderboard](https://benchlm.ai/benchmarks/swe-bench-pro)

### 2. SWE-bench Verified 子集更新

2026年8月更新的 Verified 子集（500个真实 GitHub Issue）显示：

- **Claude Fable 5**: 95.0% (最高分)
- 评估更严格: 要求完整的 PR 提交和测试通过
- 时间限制: 每个任务最多60分钟代理运行时间

> 来源: [LLM Stats - SWE-Bench Verified Leaderboard](https://llm-stats.com/benchmarks/swe-bench-verified)

### 3. ProgramBench: 从零构建软件的能力测试

2026年5月发布的 ProgramBench 关注一个全新问题：**模型能否从无到有构建有意义的软件制品？**

与传统 SWE-bench 的区别：

| 维度 | SWE-bench | ProgramBench |
|------|-----------|--------------|
| 输入 | 现有代码库 + Issue | 纯需求描述 |
| 输出 | Bug修复PR | 完整可运行应用 |
| 评估 | patch正确性 | 功能完整性 + 代码质量 |
| 场景 | 维护现有系统 | 从头开发新产品 |

> 来源: [SWE-bench 官方](https://www.swebench.com/)

---

## 评估范式演进

```
2024年: 代码补全正确率        → HUMANEVAL (60-80%)
2025年: Bug修复能力           → SWE-bench (30-60%)
2026年: 完整软件工程能力      → SWE-bench Pro / ProgramBench (70-80%)
未来:   生产环境可靠性        → 需结合CI/CD真实验证
```

---

## 对开发者的意义

1. **不要只看benchmark**: SWE-bench Pro 高分不等于实际工作能力强
2. **关注 setup check**: 部分高分依赖特殊的任务配置优化
3. **实战检验**: 真正的考核是在自己的项目中验证代理能力

---

## 参考链接

- [SWE-bench Leaderboards](https://www.swebench.com/)
- [SWE-bench Pro Leaderboard - BenchLM](https://benchlm.ai/benchmarks/swe-bench-pro)
- [SWE-Bench Verified Leaderboard - LLM Stats](https://llm-stats.com/benchmarks/swe-bench-verified)
- [AI Coding Agents August 2026 Benchmark Shakeup](https://neuralcoretech.com/ai-coding-agents-august-2026-benchmark-shakeup/)
- [BenchmarkList - SWE Bench Live](https://benchmarklist.com/benchmarks/swe_bench_live/)
