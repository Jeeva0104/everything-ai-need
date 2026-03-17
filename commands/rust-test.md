---
name: rust-test
description: Enforce TDD workflow for Rust. Write tests first, then implement. Verify 80%+ coverage.
user_invocable: true
---

# Rust TDD Command

This command enforces test-driven development methodology for Rust code using `#[test]`, rstest, proptest, and mockall.

## What This Command Does

1. **Define Types/Traits**: Scaffold function signatures with `todo!()`
2. **Write Tests**: Create comprehensive test module (RED)
3. **Run Tests**: Verify tests fail for the right reason
4. **Implement Code**: Write minimal code to pass (GREEN)
5. **Refactor**: Improve while keeping tests green
6. **Check Coverage**: Ensure 80%+ coverage with cargo-llvm-cov

## When to Use

Use `/rust-test` when:
- Implementing new Rust functions, methods, or traits
- Adding test coverage to existing Rust code
- Fixing bugs (write failing test first)
- Building critical business logic
- Learning TDD workflow in Rust

## TDD Cycle

```
RED     -> Write failing test first
GREEN   -> Implement minimal code to pass
REFACTOR -> Improve code, tests stay green
REPEAT  -> Next test case
```

## Test Patterns

### Unit Tests
```rust
#[test]
fn adds_two_numbers() {
    assert_eq!(add(2, 3), 5);
}
```

### Parameterized Tests with rstest
```rust
use rstest::rstest;

#[rstest]
#[case("hello", 5)]
#[case("", 0)]
fn test_string_length(#[case] input: &str, #[case] expected: usize) {
    assert_eq!(input.len(), expected);
}
```

### Async Tests
```rust
#[tokio::test]
async fn fetches_data_successfully() {
    let client = TestClient::new().await;
    let result = client.get("/data").await;
    assert!(result.is_ok());
}
```

## Coverage Commands

```bash
cargo llvm-cov                    # Summary
cargo llvm-cov --html             # HTML report
cargo llvm-cov --fail-under-lines 80  # Fail if below threshold
cargo test -- --nocapture         # Run with output
```

## Coverage Targets

| Code Type | Target |
|-----------|--------|
| Critical business logic | 100% |
| Public API | 90%+ |
| General code | 80%+ |
| Generated / FFI bindings | Exclude |

## TDD Best Practices

**DO:**
- Write test FIRST, before any implementation
- Run tests after each change
- Use `assert_eq!` over `assert!` for better error messages
- Use `?` in tests that return `Result`
- Test behavior, not implementation

**DON'T:**
- Write implementation before tests
- Skip the RED phase
- Use `#[should_panic]` when `Result::is_err()` works
- Use `sleep()` in tests
