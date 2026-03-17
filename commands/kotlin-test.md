---
name: kotlin-test
description: Enforce TDD workflow for Kotlin. Write Kotest tests first, then implement. Verify 80%+ coverage with Kover.
user_invocable: true
---

# Kotlin TDD Command

This command enforces test-driven development methodology for Kotlin code using Kotest, MockK, and Kover.

## What This Command Does

1. **Define Types/Interfaces**: Scaffold function signatures first
2. **Write Kotest Tests**: Create comprehensive test specs (RED)
3. **Run Tests**: Verify tests fail for the right reason
4. **Implement Code**: Write minimal code to pass (GREEN)
5. **Refactor**: Improve while keeping tests green
6. **Check Coverage**: Ensure 80%+ coverage with Kover

## When to Use

Use `/kotlin-test` when:
- Implementing new Kotlin functions or classes
- Adding test coverage to existing Kotlin code
- Fixing bugs (write failing test first)
- Building critical business logic
- Learning TDD workflow in Kotlin

## TDD Cycle

```
RED     -> Write failing Kotest test
GREEN   -> Implement minimal code to pass
REFACTOR -> Improve code, tests stay green
REPEAT  -> Next test case
```

## Coverage Targets

| Code Type | Target |
|-----------|--------|
| Critical business logic | 100% |
| Public APIs | 90%+ |
| General code | 80%+ |
| Generated code | Exclude |

## TDD Best Practices

**DO:**
- Write test FIRST, before any implementation
- Run tests after each change
- Use Kotest matchers for expressive assertions
- Use MockK's `coEvery`/`coVerify` for suspend functions
- Test behavior, not implementation details
- Include edge cases (empty, nil, max values)

**DON'T:**
- Write implementation before tests
- Skip the RED phase
- Test private functions directly
- Use `Thread.sleep()` in coroutine tests
- Ignore flaky tests

## Related Commands

- `/kotlin-build` - Fix build errors
- `/kotlin-review` - Review code after implementation
- `/verify` - Run full verification loop
