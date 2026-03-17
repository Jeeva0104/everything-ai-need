---
name: update-codemaps
description: Analyze codebase structure and generate token-lean architecture documentation.
user_invocable: true
---

# Update Codemaps Command

Analyze the codebase structure and generate token-lean architecture documentation.

## Step 1: Scan Project Structure

1. Identify project type (monorepo, single app, library, microservice)
2. Find all source directories
3. Map entry points

## Step 2: Generate Codemaps

Create/update codemaps in `docs/CODEMAPS/`:

| File | Contents |
|------|----------|
| `architecture.md` | High-level system diagram, service boundaries |
| `backend.md` | API routes, middleware chain, service mapping |
| `frontend.md` | Page tree, component hierarchy, state flow |
| `data.md` | Database tables, relationships, migrations |
| `dependencies.md` | External services, integrations |

### Format

Token-lean, optimized for AI context:

```markdown
# Backend Architecture

## Routes
POST /api/users → UserController.create → UserService.create → UserRepo.insert

## Key Files
src/services/user.ts (business logic, 120 lines)

## Dependencies
- PostgreSQL (primary data store)
- Redis (session cache)
```

## Step 3: Diff Detection

- If changes > 30%, show diff and request approval
- If changes <= 30%, update in place

## Step 4: Metadata

Add freshness header:
```markdown
<!-- Generated: 2026-02-11 | Files scanned: 142 | Token estimate: ~800 -->
```
