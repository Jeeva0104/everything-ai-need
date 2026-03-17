---
name: setup-pm
description: Set up package manager configuration for the project.
user_invocable: true
---

# Setup PM Command

Set up package manager configuration for the project.

## Detected Package Managers

| Manager | Files | Commands |
|---------|-------|----------|
| npm | package.json, package-lock.json | npm install, npm run |
| yarn | yarn.lock | yarn install, yarn run |
| pnpm | pnpm-lock.yaml | pnpm install, pnpm run |
| bun | bun.lockb | bun install, bun run |
| pip | requirements.txt | pip install -r |
| poetry | pyproject.toml, poetry.lock | poetry install |
| cargo | Cargo.toml, Cargo.lock | cargo build |

## Process

1. Detect package manager from lock files
2. Verify installation
3. Run install command
4. Check for post-install scripts
5. Verify setup

## Usage

```
/setup-pm
/setup-pm --manager npm
/setup-pm --verify
```
