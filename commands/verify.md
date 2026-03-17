---
name: verify
description: Run comprehensive verification checks on the codebase.
user_invocable: true
---

# Verify Command

Run comprehensive verification checks on the codebase.

## Usage

```
/verify [quick|full|pre-commit|pre-pr]
```

## Verification Levels

### quick
- Build check
- Type check

### full (default)
- Build check
- Type check
- Lint check
- Test suite
- Console.log audit

### pre-commit
- Build check
- Type check
- Lint check
- Test suite

### pre-pr
- All full checks
- Security scan
- Git status check

## Output Format

```
========================================
VERIFICATION REPORT
========================================

Build:    OK / FAIL
Types:    OK / X errors
Lint:     OK / X issues
Tests:    X/Y passed, Z% coverage
Secrets:  OK / X found
Logs:     OK / X console.logs
Git:      No uncommitted / X changes

Ready for PR: YES / NO
```

## Exit Codes

- `0` - All checks passed
- `1` - Critical checks failed
