---
name: tdd
description: Enforce test-driven development methodology with RED-GREEN-REFACTOR cycle.
user_invocable: true
---

# TDD Command

This command invokes the **tdd-guide** agent to enforce test-driven development methodology.

## Core Workflow

**RED → GREEN → REFACTOR** cycle:

1. **RED** - Write a failing test
2. **GREEN** - Write minimal code to pass
3. **REFACTOR** - Improve code, keep tests passing

## Key Requirements

- Write tests BEFORE implementation
- Aim for 80%+ code coverage
- 100% for critical code (financial, auth, security)
- Include unit tests for edge cases, error conditions, boundary values

## Process

1. **Scaffold interfaces** - Define types/function signatures
2. **Generate failing tests** - Write comprehensive test cases
3. **Implement minimal code** - Just enough to pass tests
4. **Verify coverage** - Ensure thresholds met

## When to Use

Use `/tdd` when:
- Starting a new feature
- Adding functionality to existing code
- Fixing bugs (write failing test first)
- Refactoring (ensure tests pass before and after)

## Coverage Targets

| Code Type | Target |
|-----------|--------|
| Critical business logic | 100% |
| Financial calculations | 100% |
| Authentication/authorization | 100% |
| Security logic | 100% |
| Public APIs | 90%+ |
| General code | 80%+ |
