---
name: refactor-clean
description: Safely identify and remove dead code with test verification at every step.
user_invocable: true
---

# Refactor Clean Command

Safely identify and remove dead code with test verification at every step.

## Step 1: Detect Dead Code

Run analysis tools based on project type:

| Tool | What It Finds | Command |
|------|--------------|---------|
| knip | Unused exports, files, dependencies | `npx knip` |
| depcheck | Unused npm dependencies | `npx depcheck` |
| ts-prune | Unused TypeScript exports | `npx ts-prune` |
| vulture | Unused Python code | `vulture src/` |
| deadcode | Unused Go code | `deadcode ./...` |
| cargo-udeps | Unused Rust dependencies | `cargo +nightly udeps` |

## Step 2: Categorize Findings

| Tier | Examples | Action |
|------|----------|--------|
| **SAFE** | Unused utilities, test helpers | Delete with confidence |
| **CAUTION** | Components, API routes | Verify no dynamic imports |
| **DANGER** | Config files, entry points | Investigate before touching |

## Step 3: Safe Deletion Loop

For each SAFE item:
1. Run full test suite - Establish baseline
2. Delete the dead code
3. Re-run test suite - Verify nothing broke
4. If tests fail - Revert and skip
5. If tests pass - Move to next item

## Rules

- Never delete without running tests first
- One deletion at a time
- Skip if uncertain
- Don't refactor while cleaning
