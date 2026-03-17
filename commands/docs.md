---
name: docs
description: Look up current documentation for libraries and frameworks.
user_invocable: true
---

# Docs Command

Look up current documentation for libraries and frameworks via Context7 MCP tools.

## Usage

```
/docs "<library>" "<question>"
/docs "Next.js" "How do I configure middleware?"
/docs "React" "useEffect cleanup function"
/docs "TypeScript" "generic constraints"
```

## Workflow

1. Resolve library ID using `resolve-library-id`
2. Query documentation using `query-docs`
3. Return summarized answer with code snippets

## Fallback

If Context7 is unavailable, answer from training data with a caveat that docs may be outdated.
