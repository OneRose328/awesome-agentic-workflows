---
on:
  issues:
    types: [opened]
permissions:
  issues: read
tools:
  github:
    toolsets: [issues, labels]
network: defaults
safe-outputs:
  add-labels:
    max: 3
  add-comment:
    max: 1
---

# Issue Intake

Classify new issues quickly so maintainers can see what needs follow-up.

## Instructions

1. Read the issue title, body, and any form fields.
2. Decide whether the issue is a bug, feature request, support question, or escalation.
3. Propose the smallest useful routing action.
4. Use safe outputs to apply labels or add one concise follow-up comment when clarification is needed.
5. If the issue is ambiguous, explain what information is missing instead of guessing.

## Notes

- Replace the label names with your repository labels.
- Tighten the `safe-outputs` limits if you want even stricter controls.

