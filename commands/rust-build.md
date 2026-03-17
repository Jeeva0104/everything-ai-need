---
name: rust-build
description: Fix Rust build errors, borrow checker issues, and dependency problems incrementally.
user_invocable: true
---

# Rust Build and Fix

This command invokes the **rust-build-resolver** agent to incrementally fix Rust build errors with minimal changes.

## What This Command Does

1. **Run Diagnostics**: Execute `cargo check`, `cargo clippy`, `cargo fmt --check`
2. **Parse Errors**: Identify error codes and affected files
3. **Fix Incrementally**: One error at a time
4. **Verify Each Fix**: Re-run `cargo check` after each change
5. **Report Summary**: Show what was fixed and what remains

## When to Use

Use `/rust-build` when:
- `cargo build` or `cargo check` fails with errors
- `cargo clippy` reports warnings
- Borrow checker or lifetime errors block compilation
- Cargo dependency resolution fails
- After pulling changes that break the build

## Common Errors Fixed

| Error | Typical Fix |
|-------|-------------|
| `cannot borrow as mutable` | Restructure to end immutable borrow first |
| `does not live long enough` | Use owned type or add lifetime annotation |
| `cannot move out of` | Restructure to take ownership |
| `mismatched types` | Add `.into()`, `as`, or explicit conversion |
| `trait X not implemented` | Add `#[derive(Trait)]` or implement manually |
| `unresolved import` | Add to Cargo.toml or fix `use` path |
| `cannot find value` | Add import or fix path |

## Fix Strategy

1. **Build errors first** - Code must compile
2. **Clippy warnings second** - Fix suspicious constructs
3. **Formatting third** - `cargo fmt` compliance
4. **One fix at a time** - Verify each change
5. **Minimal changes** - Don't refactor, just fix

## Stop Conditions

The agent will stop and report if:
- Same error persists after 3 attempts
- Fix introduces more errors
- Requires architectural changes
- Borrow checker error requires redesigning data ownership

## Related Commands

- `/rust-test` - Run tests after build succeeds
- `/rust-review` - Review code quality
- `/verify` - Full verification loop
