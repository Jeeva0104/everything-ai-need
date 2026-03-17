---
name: evolve
description: Analyze instincts and suggest or generate evolved structures.
user_invocable: true
---

# Evolve Command

Analyze instincts and suggest or generate evolved structures (commands, skills, agents).

## Usage

```bash
/evolve [--generate]
```

## Evolution Types

1. **Commands** - User-invoked actions from repeated instinct sequences
2. **Skills** - Auto-triggered behaviors from related patterns
3. **Agents** - Complex multi-step processes

## Process

1. Cluster related instincts by trigger patterns
2. Identify high-confidence sequences
3. Suggest evolutions:
   - Command: Repeated manual sequences
   - Skill: Auto-triggered patterns
   - Agent: Complex multi-step workflows

## Output

```
EVOLUTION ANALYSIS
==================
Instincts analyzed: N
Clusters found: M

Suggested Commands:
- cmd1 (confidence: X%)
- cmd2 (confidence: Y%)

Suggested Skills:
- skill1 (confidence: Z%)

Suggested Agents:
- agent1 (confidence: W%)
```

With `--generate` flag, creates files in `evolved/{skills,commands,agents}/`.
