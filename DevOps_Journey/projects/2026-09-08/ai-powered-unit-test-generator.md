# Project: AI-Powered Unit Test Generator

## Overview
Create a tool that analyzes source code and automatically generates comprehensive unit tests, including edge cases, boundary conditions, and integration test scenarios.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────────────┐
│              Test Generator                                  │
│  ┌─────────────┐  ┌─────────────┐  ┌──────────────────┐   │
│  │ AST         │  │ Test        │  │ Coverage        │   │
│  │ Analyzer    │  │ Generator   │  │ Optimizer       │   │
│  └─────────────┘  └─────────────┘  └──────────────────┘   │
│                                                           │
│  ┌─────────────────────────────────────────────────────┐  │
│  │           Test Executor & Validator                  │  │
│  │  · Run tests · Check coverage · Report gaps         │  │
│  └─────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

## Workflow
1. **Parse**: Analyze function signatures and types
2. **Understand**: Infer business logic from code
3. **Generate**: Create test cases
4. **Execute**: Run generated tests
5. **Evaluate**: Measure coverage and quality
6. **Improve**: Refine based on feedback

## Tools
- Python (ast module)
- pytest/unittest frameworks
- LLM API for test logic
- Coverage.py for metrics
- GitHub Actions for CI

## Learning Goals
- Static analysis techniques
- Test-driven development
- Code coverage metrics
- LLM-based code generation

## Build Milestones
1. Week 1: AST analyzer
2. Week 2: Test case generator
3. Week 3: Execution framework
4. Week 4: Coverage analysis
5. Week 5: Edge case detection
6. Week 6: CI integration
