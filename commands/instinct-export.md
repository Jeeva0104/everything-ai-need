---
name: instinct-export
description: Export learned instincts to YAML for sharing, backup, or migration.
user_invocable: true
---

# Instinct Export Command

Export learned instincts from current project or global scope to a YAML file.

## Usage

```
/instinct-export [path] [--scope project|global] [--domain <domain>] [--min-confidence <0-100>]
```

## Options

- `path` - Output file path (default: `instincts-export.yaml`)
- `--scope` - Export `project` (default) or `global` instincts
- `--domain` - Filter by domain (e.g., `rust`, `security`, `workflow`)
- `--min-confidence` - Only export instincts above confidence threshold

## Examples

```
/instinct-export                    # Export project instincts
/instinct-export --scope global     # Export global instincts
/instinct-export --domain rust      # Export only Rust-related instincts
/instinct-export --min-confidence 80 # Only high-confidence instincts
```

## Implementation

```bash
python3 "${CLAUDE_PLUGIN_ROOT}/skills/continuous-learning-v2/scripts/instinct-cli.py" export "$@"
```

## Output Format

Exports as YAML with metadata:
```yaml
export_metadata:
  timestamp: 2026-03-16T10:30:00Z
  scope: project
  project_id: abc123def456
  project_name: my-rust-app
  total_instincts: 15

instincts:
  - id: rust-error-handling-001
    pattern: "Handle Result with match or ? operator"
    confidence: 92
    domain: rust
    observations: 47
    triggers:
      - "when writing Rust functions that return Result"
```
