---
name: build-fix
description: Systematically fix build errors with minimal changes.
user_invocable: true
---

# Build Fix

Systematically fix build errors with minimal changes. Detects build system, parses errors, and fixes incrementally.

## Usage

```bash
/build-fix [scope]
```

## Process

### Step 1: Detect Build System

| Build Tool | Detection | Command |
|------------|-----------|---------|
| npm/yarn/pnpm | package.json exists | `npm run build` |
| TypeScript | tsconfig.json exists | `tsc --noEmit` |
| Next.js | next.config.* exists | `next build` |
| Vite | vite.config.* exists | `vite build` |
| Rust/Cargo | Cargo.toml exists | `cargo build` |
| Go | go.mod exists | `go build ./...` |
| Python | pyproject.toml or setup.py | `python -m build` |

### Step 2: Parse and Group Errors

1. Run the build command
2. Capture stderr output
3. Parse errors by:
   - File path
   - Line number
   - Error message
   - Severity (error vs warning)
4. Group by file
5. Sort by dependency order (fix leaf files first)

### Step 3: Fix Loop

For each error group:

1. Read the file
2. Analyze the error context
3. Apply minimal fix
4. Re-run build
5. Verify fix worked
6. Move to next error

### Step 4: Guardrails

- **Stop if**: Fix introduces more errors
- **Stop if**: Same error persists after 3 attempts
- **Stop if**: Requires structural/architectural changes
- **Stop if**: Missing external dependencies

### Step 5: Summary

Report results:
```
BUILD FIX COMPLETE
==================
Build system: [detected]
Errors fixed: N
Warnings fixed: M
Files modified: X
Remaining issues: Y

Build status: ✅ PASS / ❌ FAIL (Y issues remain)
```

## Recovery Strategies

| Error Type | Fix Strategy |
|------------|--------------|
| Missing import | Add correct import |
| Type mismatch | Cast or fix type |
| Undefined variable | Define or import |
| Syntax error | Fix syntax |
| Missing dependency | Install or mock |
| Config error | Fix config file |

## Arguments

$ARGUMENTS:
- `[scope]` - Optional scope (e.g., "frontend", "backend", "all")
