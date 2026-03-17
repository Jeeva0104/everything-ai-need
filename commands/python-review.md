---
name: python-review
description: Comprehensive Python code review with type checking, linting, and security analysis.
user_invocable: true
---

# Python Review Command

This command invokes the **python-reviewer** agent for comprehensive Python-specific code review.

## What This Command Does

1. **Identify Python Changes**: Find modified `.py` files via `git diff`
2. **Run Type Checks**: Execute `mypy` for static type analysis
3. **Run Linters**: Execute `ruff`, `pylint`, or `flake8`
4. **Security Scan**: Check for injection vulnerabilities, unsafe eval, hardcoded secrets
5. **Check Imports**: Verify no circular imports, unused imports
6. **Generate Report**: Categorize issues by severity

## When to Use

Use `/python-review` when:
- After writing or modifying Python code
- Before committing Python changes
- Reviewing pull requests with Python code
- Onboarding to a new Python codebase

## Review Categories

### CRITICAL (Must Fix)
- SQL injection vulnerabilities
- Command injection (unsafe `os.system`, `subprocess`)
- Hardcoded credentials/API keys
- Unsafe `eval()` or `exec()` usage
- Missing input validation

### HIGH (Should Fix)
- Type errors (mypy failures)
- Undefined variables
- Unused imports
- Functions > 50 lines
- Missing docstrings on public APIs

### MEDIUM (Consider)
- Non-idiomatic Python patterns
- Missing type hints
- Inefficient list operations
- Style violations

## Automated Checks Run

```bash
# Type checking
mypy src/

# Linting
ruff check src/

# Security
bandit -r src/

# Format checking
black --check src/
```

## Approval Criteria

| Status | Condition |
|--------|-----------|
| ✅ Approve | No CRITICAL or HIGH issues |
| ⚠️ Warning | Only MEDIUM issues |
| ❌ Block | CRITICAL or HIGH issues found |
