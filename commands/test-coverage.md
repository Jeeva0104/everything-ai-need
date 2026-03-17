---
name: test-coverage
description: Analyze and improve test coverage for the codebase.
user_invocable: true
---

# Test Coverage Command

Analyze and improve test coverage for the codebase.

## Process

### Step 1: Detect Test Framework

Identify the testing framework from project files:
- `package.json` → Jest, Vitest, Mocha
- `Cargo.toml` → cargo test
- `go.mod` → go test
- `pyproject.toml` → pytest

### Step 2: Analyze Coverage Report

Run coverage analysis:
```bash
# JavaScript/TypeScript
npx vitest run --coverage

# Rust
cargo llvm-cov

# Go
go test -cover ./...

# Python
pytest --cov=src
```

### Step 3: Identify Under-Covered Files

Find files with < 80% coverage and categorize:
- Missing happy path tests
- Missing error handling tests
- Missing edge case tests
- Missing branch coverage

### Step 4: Generate Missing Tests

For each under-covered file:
1. Read the source file
2. Identify untested functions/branches
3. Write tests following existing patterns
4. Prioritize by:
   - Critical business logic first
   - Error paths second
   - Edge cases third

## Rules

- Add tests to existing test files when possible
- Match existing test patterns and naming
- Mock external dependencies
- Use descriptive test names
