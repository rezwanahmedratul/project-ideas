# Project: Automated API Test Suite Generator

## Overview
Create a tool that analyzes API specifications (OpenAPI/Swagger) and automatically generates comprehensive test suites including positive/negative cases, edge cases, and performance tests.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────┐
│     Automated API Test Generator                    │
├─────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐ │
│  │  Spec       │  │  Test       │  │  Execution  │ │
│  │  Parser     │  │  Generator  │  │  & Report   │ │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘ │
│         │                 │                 │        │
│         └─────────────────┼─────────────────┘        │
│                           ▼                          │
│                 ┌─────────────────┐                 │
│                 │  Test Categories│                 │
│                 │  • Positive     │                 │
│                 │  • Negative     │                 │
│                 │  • Edge Cases   │                 │
│                 └─────────────────┘                 │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Input: OpenAPI/Swagger specification file
2. Parse all endpoints, schemas, and parameters
3. Generate test cases for each endpoint:
   - **Positive**: Valid requests with correct payloads
   - **Negative**: Invalid inputs, missing fields, wrong types
   - **Edge Cases**: Boundary values, large payloads, special chars
   - **Auth**: Token validation, permission checks
   - **Performance**: Response time, throughput tests
4. Output: Ready-to-run test suites in pytest/Playwright/Jest
5. Execute tests and generate coverage reports
6. Track test coverage over time as API evolves

## Tools
- Python with prance or swagger-parser
- Pytest or Jest for test execution
- Locust or k6 for performance testing
- GitHub Actions for CI integration
- Allure or HTML for report generation

## Learning Goals
- API testing methodologies
- OpenAPI specification understanding
- Test case generation algorithms
- Performance testing basics
- CI/CD test automation

## Build Milestones
1. **Week 1**: Spec parser + endpoint extraction
2. **Week 2**: Generate positive test cases
3. **Week 3**: Add negative and edge case generators
4. **Week 4**: Implement auth and permission tests
5. **Week 5**: Add performance testing capabilities
6. **Week 6**: Create reporting and CI integration
