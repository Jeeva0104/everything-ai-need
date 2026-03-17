---
name: skill-create
description: Analyze local git history to extract coding patterns and generate SKILL.md files.
user_invocable: true
---

# Skill Create Command

Analyze your repository's git history to extract coding patterns and generate SKILL.md files.

## Usage

```
/skill-create                    # Analyze current repo
/skill-create --commits 100      # Analyze last 100 commits
/skill-create --output ./skills  # Custom output directory
/skill-create --instincts        # Also generate instincts
```

## What It Does

1. **Parses Git History** - Analyzes commits, file changes, and patterns
2. **Detects Patterns** - Identifies recurring workflows and conventions
3. **Generates SKILL.md** - Creates valid Claude Code skill files
4. **Optionally Creates Instincts** - For the continuous-learning-v2 system

## Analysis Steps

### Step 1: Gather Git Data

```bash
git log --oneline -n 200 --name-only --pretty=format:"%H|%s|%ad" --date=short
git log --oneline -n 200 --name-only | grep -v "^$" | sort | uniq -c | sort -rn | head -20
```

### Step 2: Detect Patterns

| Pattern | Detection Method |
|---------|-----------------|
| Commit conventions | Regex on commit messages |
| File co-changes | Files that always change together |
| Workflow sequences | Repeated file change patterns |
| Architecture | Folder structure and naming |
| Testing patterns | Test file locations, naming |

## Output Format

```markdown
---
name: {repo-name}-patterns
description: Coding patterns extracted from {repo-name}
version: 1.0.0
source: local-git-analysis
analyzed_commits: {count}
---

# {Repo Name} Patterns

## Commit Conventions
## Code Architecture
## Workflows
## Testing Patterns
```

## Related

- `/instinct-import` - Import generated instincts
- `/instinct-status` - View learned instincts
- `/evolve` - Cluster instincts into skills
