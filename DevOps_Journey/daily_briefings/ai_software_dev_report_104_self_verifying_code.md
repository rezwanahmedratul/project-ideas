# AI Software Dev Report #104 — Self-Verifying Code & AI-Generated Test Suites

## Overview
As AI-generated code adoption accelerates, ensuring correctness and reliability has become a critical challenge. Self-verifying code systems and AI-augmented test generation are emerging as essential practices for shipping AI-written software with confidence.

## The Verification Problem
- ~41% of code written in 2025 was AI-generated
- LLMs can produce plausible but incorrect code (hallucinated APIs, subtle logic errors)
- Traditional testing alone cannot catch all AI-specific failure modes

## Approaches

### AI-Generated Test Suites
- Tools automatically generate unit, integration, and edge-case tests from code descriptions
- **Claude Code**, **Cursor Agent**, and **GitHub Copilot** can generate comprehensive test coverage
- Prompt engineering patterns for test generation: specify boundary conditions, error paths, and property-based tests

### Self-Verifying Code Patterns
1. **Contract Testing** — Define input/output contracts; AI generates tests that enforce them
2. **Property-Based Testing** — Describe invariants rather than specific inputs; tools like Hypothesis (Python) or fast-check (JS) auto-generate cases
3. **Fuzzing Integration** — AI-generated code tested against randomized inputs via AFL++, libFuzzer
4. **Round-Trip Verification** — Generate → Execute → Inspect → Regenerate on failure

### Automated Code Review
- **GitHub Advanced Security** — AI-powered PR analysis
- **CodeRabbit** — AI code review assistant
- **SonarQube + AI** — Static analysis with AI-enhanced findings

## Best Practices for Developers
- Always audit AI-generated code before merging
- Use AI to write tests first, then code (test-driven AI development)
- Implement CI gates that reject AI-generated code without adequate test coverage
- Maintain human review for security-sensitive modules

## Reference Links
- [Self-Verifying Agents in Production](../daily_briefings/ai_software_dev_report_9_self_verifying_agents.md)
- [Automated Testing with AI — GitHub Blog](https://github.blog/)
- [Property-Based Testing with Hypothesis](https://hypothesis.works/)
- [CodeRabbit AI Code Review](https://coderabbit.ai/)
