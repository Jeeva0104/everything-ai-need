---
name: eval
description: Run skill or command evaluation with red-teaming and adversarial testing.
user_invocable: true
---

# Eval Command

Run skill or command evaluation with red-teaming and adversarial testing.

## Usage

```
/eval <skill-name|command-name>
/eval tdd-workflow
/eval code-review
```

## Process

1. Load the skill/command spec
2. Generate adversarial test cases
3. Execute tests
4. Measure success rate
5. Report findings

## Output

```
EVALUATION REPORT: <name>
==============================
Test cases: N
Passed: X
Failed: Y
Success rate: Z%

Red-team findings:
- Finding 1
- Finding 2

Recommendations:
- Rec 1
- Rec 2
```
