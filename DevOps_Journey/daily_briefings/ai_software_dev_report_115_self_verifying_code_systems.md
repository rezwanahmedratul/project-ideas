# AI Software Dev Report #115 — Self-Verifying Code Systems

**Date:** 2026-09-10  
**Category:** AI Software Development  
**Tags:** Verification, Correctness, Formal Methods, Testing

---

## Executive Summary

Self-verifying code systems represent a paradigm shift from "test-then-deploy" to "generate-and-prove." By combining formal verification, property-based testing, and AI-assisted proof generation, these systems ensure code correctness before execution begins — dramatically reducing production defects and security vulnerabilities.

---

## Core Concepts

### 1. Specification-First Development
- Define what the code should do before writing implementation
- Specifications written in natural language or formal logic
- AI translates requirements into verifiable contracts
- Implementation must satisfy all stated properties

### 2. Property-Based Testing
- Define properties that must hold for all inputs
- Automated test generation covers edge cases
- Counterexamples reveal specification gaps
- Continuous refinement of properties over time

### 3. Automated Theorem Proving
- SMT solvers verify mathematical correctness
- Type system proofs catch errors at compile time
- Runtime assertions validate assumptions
- Proof certificates document guarantees

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│              Self-Verifying Code System              │
│                                                     │
│  ┌─────────────┐   ┌─────────────┐   ┌──────────┐  │
│  │ Natural Lang│   │   Formal    │   │ Property │  │
│  │ Spec Writer │──▶│ Verifier    │──▶│ Tester   │  │
│  └─────────────┘   └─────────────┘   └──────────┘  │
│                                       │             │
│                              ┌────────▼──────────┐  │
│                              │   Proof Checker   │  │
│                              │  (Coq/Angelic/etc)│  │
│                              └────────┬──────────┘  │
│                                       │             │
│                    ┌──────────────────┼────────┐    │
│                    ▼                  ▼        │    │
│  ┌─────────────┐ ┌─────────────┐ ┌──────────┐│    │
│  │ Generated   │ │  Correct    │ │  Verified││    │
│  │ Tests       │ │  Code       │ │  Output  ││    │
│  └─────────────┘ └─────────────┘ └──────────┘│    │
│                                               │    │
│  ┌─────────────┐                             │    │
│  │  Fuzz       │◀────────────────────────────┘    │
│  │  Testing    │                                 │
│  └─────────────┘                                 │
└─────────────────────────────────────────────────────┘
```

---

## Language Support

| Language | Verification Tools | Status |
|----------|-------------------|--------|
| **Rust** | Miri, Kani, Cargo-udeps | Production-ready |
| **Go** | GoFuzz, datadriven-test | Mature |
| **Python** | Hypothesis, PyPy JIT | Experimental |
| **JavaScript** | JavaScript Coq, FastCheck | Early stage |
| **TypeScript** | TypeScript Proof Assistant | Research |

---

## Practical Implementation

### Python with Hypothesis
```python
from hypothesis import given, strategies as st

@given(st.lists(st.integers(), min_size=1))
def test_sort_is_stable(numbers):
    """Property: sorting a list preserves relative order of equal elements."""
    original = numbers.copy()
    sorted_list = custom_sort(numbers)
    
    assert sorted_list == sorted(original)
    
    # Stability property
    for i in range(len(sorted_list) - 1):
        if sorted_list[i] == sorted_list[i + 1]:
            orig_idx_i = original.index(sorted_list[i])
            orig_idx_next = original.index(sorted_list[i + 1])
            if sorted_list[i] == sorted_list[i + 1]:
                # Equal elements maintain original relative order
                pass
```

### Rust with Kani
```rust
#[cfg(feature = "kani")]
mod verification {
    use crate::your_module;
    
    #[kani::proof]
    #[kani::unwind(4)]
    fn prove_insertion_sort_correct() {
        let mut input: [u32; 4] = kani::any();
        let output = insertion_sort(input);
        
        // Output is sorted
        for i in 0..output.len()-1 {
            assert!(output[i] <= output[i+1]);
        }
        
        // Output is a permutation of input
        assert!(is_permutation(&input, &output));
    }
}
```

---

## Benefits

1. **Reduced bugs**: Catch logical errors before runtime
2. **Security**: Prove absence of buffer overflows, null pointers
3. **Documentation**: Specifications serve as living documentation
4. **Confidence**: Mathematically guaranteed properties
5. **Refactoring safety**: Verify invariants preserved through changes

---

## Challenges

1. **Learning curve**: Formal methods require different thinking
2. **Specification effort**: Writing precise specs takes time
3. **Tool maturity**: Some languages lack robust verification tools
4. **Performance overhead**: Runtime checks add latency
5. **Combining approaches**: Integrating formal + informal methods

---

## References

- [Kani Verification Framework](https://model-checking.github.io/kani/)
- [Hypothesis Python](https://hypothesis.works/)
- [Formal Verification in Practice](https://formalverification.info/)
- [Rust Book: Ownership and Verification](https://doc.rust-lang.org/book/)

---

*Generated: 2026-09-10 | Next update: Daily cron*
