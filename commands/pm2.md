---
name: pm2
description: Analyze project and generate PM2 service management configuration.
user_invocable: true
---

# PM2 Command

Automatically analyze a project and generate PM2 service management commands.

## Service Detection

Identifies frameworks and assigns ports:
- Vite (5173)
- Next.js (3000)
- Nuxt (3000)
- CRA (3000)
- Express (3000)
- FastAPI/Flask (8000)
- Go (8080)

## Generated Files

- `ecosystem.config.cjs` - PM2 configuration
- `{backend}/start.cjs` - Python wrapper script
- `.claude/commands/` - Various PM2 command files
- `.claude/scripts/` - PowerShell log scripts

## Windows-Specific Requirements

- Must use `.cjs` extension
- Specify full Node.js bin paths
- Python uses Node.js wrapper with `windowsHide: true`
- New terminal windows use `start wt.exe`

## Workflow

Scan → Generate config → Generate commands → Update CLAUDE.md → Display summary
