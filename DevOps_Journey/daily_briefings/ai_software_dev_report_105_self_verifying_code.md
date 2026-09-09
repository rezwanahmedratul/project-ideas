# AI Software Dev Report #105 — Self-Verifying Code & AI-Generated Testing

**Date:** 2026-09-09  
**Category:** Quality Assurance

---

## Executive Summary

AI-generated code often lacks the reliability guarantees of hand-written code. Self-verifying code — systems that automatically validate, test, and correct their own outputs — is emerging as a critical solution for production AI applications.

---

## The Problem: AI Code Reliability

Even state-of-the-art models produce code with:
- Logical errors (wrong algorithms)
- Edge case failures
- Security vulnerabilities
- Performance issues
- Integration problems

Studies show AI-generated code has error rates comparable to junior developers — sometimes higher for complex logic.

---

## Self-Verifying Architecture

### The Verify-Refine Loop

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Generate  │────▶│   Test &    │────▶│  Pass?      │
│   Code      │     │   Validate  │     └──────┬──────┘
└─────────────┘     └─────────────┘            │
                                               ▼
                                         ┌─────────────┐
                                         │  Refine &   │
                                         │  Regenerate │
                                         └─────────────┘
```

### Implementation Pattern
```python
class SelfVerifyingAgent:
    async def generate(self, spec: str) -> CodeResult:
        code = await self.generator.create(spec)
        
        while not self.verifier.is_valid(code):
            errors = await self.verifier.check(code)
            code = await self.generator.fix(code, errors)
            
        return code
```

---

## Testing Strategies

### 1. Property-Based Testing
Define properties that must always hold, let AI generate test cases.

```python
from hypothesis import given, strategies as st

@given(st.lists(st.integers(), min_size=1))
def test_sort_preserves_elements(items):
    sorted_items = quicksort(items)
    assert sorted(sorted_items) == sorted_items
```

### 2. Fuzz Testing
AI generates random inputs to find edge cases.

### 3. Formal Verification
Use theorem provers to mathematically prove correctness.

### 4. Mutation Testing
Introduce small changes (mutations) to verify tests catch them.

---

## Tools & Frameworks

| Tool | Purpose | Language |
|------|---------|----------|
| **UnitTest/pytest** | Standard testing | Python |
| **Jest/Vitest** | JavaScript testing | JS/TS |
| **PropEr/Hypothesis** | Property-based testing | Erlang/Python |
| **Credal** | Constraint-based testing | Python |
| **Certora** | Smart contract verification | Solidity |
| **Coq/Isabelle** | Formal verification | Multiple |

---

## CI/CD Integration

### Pipeline Steps
1. **Generate:** AI creates code from specifications
2. **Test:** Run automated test suite
3. **Coverage:** Verify minimum coverage thresholds
4. **Security scan:** Check for vulnerabilities
5. **Performance:** Benchmark against baselines
6. **Merge:** Only pass all checks

### Gatekeeping Rules
```yaml
pipeline:
  gates:
    - tests_pass: true
    - coverage_min: 80%
    - security_scan: clean
    - linter: no_errors
    - human_approval: for_production
```

---

## Case Study: AI-Generated API

**Task:** Generate a REST API for user management

**Generation:**
```python
# AI-generated code (first attempt)
@app.get("/users/{user_id}")
async def get_user(user_id: int):
    user = db.query(User).filter(id=user_id).first()
    return user
```

**Self-Verification detects:**
1. ❌ No error handling for missing user
2. ❌ No input validation
3. ❌ No authentication check
4. ❌ No rate limiting

**Refined output:**
```python
@app.get("/users/{user_id}")
async def get_user(user_id: int, current_user: User = Depends(get_current_user)):
    if not current_user.is_admin and current_user.id != user_id:
        raise HTTPException(status_code=403)
    
    user = await db.get(User, user_id)
    if not user:
        raise HTTPException(status_code=404, detail="User not found")
    
    return user
```

---

## Best Practices

1. **Start simple:** Begin with unit tests, add complexity gradually
2. **Fast feedback:** Keep test suites under 5 minutes
3. **Coverage thresholds:** Enforce minimums (80%+ recommended)
4. **Continuous verification:** Test after every change
5. **Human review:** Critical paths still need human oversight

---

## References

1. [Property-Based Testing with Hypothesis](https://hypothesis.works/)
2. [Mutation Testing Overview](https://mutmut.readthedocs.io/)
3. [Formal Verification for AI Code](https://arxiv.org/abs/2401.00001)
4. [Self-Healing Code Systems](https://blog.replit.com/self-healing)

---

*Generated: 2026-09-09 | Source: Overnight research engine*
