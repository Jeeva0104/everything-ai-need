---
name: rust-review
description: Comprehensive Rust code review for ownership, lifetimes, error handling, and idiomatic patterns.
user_invocable: true
---

# Rust Code Review Command

This command invokes the **rust-reviewer** agent to analyze code for issues related to ownership, lifetimes, error handling, unsafe usage, and idiomatic Rust patterns.

## What This Command Does

1. **Identify Rust Changes**: Find modified `.rs` files via `git diff`
2. **Run Static Analysis**: Execute `cargo check`, `cargo clippy`, `cargo fmt`
3. **Security Scan**: Check for unsafe usage, unwrap/expect patterns
4. **Ownership Review**: Analyze borrow patterns, lifetime annotations
5. **Error Handling Review**: Check Result/Option usage, error propagation
6. **Generate Report**: Categorize issues by severity

## When to Use

Use `/rust-review` when:
- After writing or modifying Rust code
- Before committing Rust changes
- Reviewing pull requests with Rust code
- Onboarding to a new Rust codebase

## Review Categories

### CRITICAL (Must Fix)
- Memory safety violations in unsafe blocks
- Unwrap/expect on user-controlled data
- Unsound lifetime annotations
- Hardcoded credentials
- Ignored Results in critical paths

### HIGH (Should Fix)
- Clone-heavy code (should use references)
- Missing error context with `anyhow`/`thiserror`
- Blocking calls in async contexts
- Unnecessary mutex usage
- Missing Send/Sync bounds

### MEDIUM (Consider)
- Non-idiomatic patterns
- Missing docs on public APIs
- Inefficient String operations
- Could use iterators instead of loops
- Missing `#![forbid(unsafe_code)]` in non-unsafe crates

## Automated Checks Run

```bash
# Static analysis
cargo check
cargo clippy -- -D warnings
cargo fmt --check

# Security
cargo audit

# Tests
cargo test
```

## Approval Criteria

| Status | Condition |
|--------|-----------|
| ✅ Approve | No CRITICAL or HIGH issues |
| ⚠️ Warning | Only MEDIUM issues |
| ❌ Block | CRITICAL or HIGH issues found |

## Related Commands

- `/rust-build` - Fix build errors
- `/rust-test` - Run TDD workflow
- `/verify` - Full verification loop
