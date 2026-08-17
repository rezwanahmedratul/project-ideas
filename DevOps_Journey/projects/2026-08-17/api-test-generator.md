# Project: Automated API Test Generator from OpenAPI Specs

## Overview
Develop a tool that parses OpenAPI/Swagger specifications and generates comprehensive test suites including unit tests, integration tests, and edge case coverage using Python pytest.

## Architecture
```
OpenAPI Spec → Parser → Test Template Generator → Test Runner
                                    ↓
                           Coverage Analysis
                                    ↓
                           Report Generation
```

## Workflow
1. Parse OpenAPI 3.0 specification
2. Extract endpoints, schemas, constraints
3. Generate parameter combinations based on constraints
4. Create pytest test cases for each endpoint
5. Add negative test cases (invalid inputs, missing fields)
6. Run tests against live/stubbed API
7. Generate coverage reports

## Tools
- **Python 3.11+**
- **OpenAPI spec-parser** or **prance**
- **pytest** with **pytest-cov** for testing framework
- **Faker** for generating test data
- **responses** library for mocking HTTP requests

## Learning Goals
- Deep understanding of REST API design
- Test-driven development practices
- Property-based testing concepts
- API security testing basics

## Build Milestones
- [ ] Week 1: OpenAPI parser and schema extraction
- [ ] Week 2: Basic positive test generation
- [ ] Week 3: Negative test and edge case generation
- [ ] Week 4: Integration with pytest and reporting
- [ ] Week 5: Advanced features (auth tests, performance baselines)

## Estimated Time
2-3 weeks (part-time)

## Difficulty
Beginner-Intermediate — great for learning API testing
