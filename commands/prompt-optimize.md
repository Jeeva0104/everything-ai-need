---
name: prompt-optimize
description: Optimize prompts for better AI model performance using 6-phase analysis.
user_invocable: true
---

# Prompt Optimize Command

Optimize prompts for better AI model performance using 6-phase analysis.

## 6-Phase Analysis

1. **Project Detection** - Identify tech stack and context
2. **Intent Detection** - Classify the request type
3. **Scope Assessment** - Determine complexity level
4. **ECC Component Matching** - Match to skills, agents, model tiers
5. **Missing Context Detection** - Identify gaps in input
6. **Output Generation** - Produce optimized prompt

## Output Format

### Full Version
```
## Diagnosis
- Intent: [Classified]
- Complexity: [TRIVIAL/LOW/MEDIUM/HIGH/EPIC]
- Recommended components: [Skills, agents, model]

## Optimized Prompt
[Full detailed version]
```

### Quick Version
```
**Intent:** [One-line classification]
**Complexity:** [Level]
**Model:** [Recommended]
```

## Usage

```
/prompt-optimize "<your prompt here>"
```
