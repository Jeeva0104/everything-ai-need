---
name: instinct-import
description: Import instincts from YAML file into project or global scope.
user_invocable: true
---

# Instinct Import Command

Import instincts from YAML file into current project or global scope.

## Usage

```
/instinct-import <path> [--scope project|global] [--dry-run] [--force]
```

## Options

- `path` - Path to YAML file to import
- `--scope` - Import to `project` (default) or `global`
- `--dry-run` - Show what would be imported without making changes
- `--force` - Overwrite existing instincts with same ID
- `--min-confidence` - Skip instincts below threshold

## Examples

```
/instinct-import instincts-export.yaml
/instinct-import instincts.yaml --scope global
/instinct-import instincts.yaml --dry-run
/instinct-import instincts.yaml --force --min-confidence 70
```

## Merge Behavior

When importing:
1. Check for duplicate instinct IDs
2. If same ID exists:
   - Keep higher confidence version
   - Or use `--force` to overwrite
3. Add source tracking metadata
4. Update observation counts

## Output

```
Import Results:
- Added: 12 new instincts
- Updated: 3 existing instincts (higher confidence)
- Skipped: 5 duplicates (lower confidence)
- Errors: 0

Total instincts after import: 47
```
