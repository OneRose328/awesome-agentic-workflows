---
on:
  pull_request:
    types: [opened, reopened, synchronize, ready_for_review]
permissions:
  contents: read
  pull-requests: read
tools:
  github:
    toolsets: [repos, pull_requests]
network: defaults
safe-outputs:
  add-comment:
    max: 2
---

# Complexity Analyzer

## Purpose
Highlight logic that is becoming too complex to reason about, review safely, or maintain without regressions.

## Trigger
Run when a pull request introduces large functions, deeply nested branching, cross-cutting side effects, or mixed responsibilities.

## Instructions
1. Inspect the changed logic for complexity signals such as deep nesting, wide branching, hidden state mutation, long conditional chains, flag-driven behavior, or multiple responsibilities inside one unit.
2. Distinguish necessary domain complexity from avoidable implementation complexity introduced by the current change.
3. Flag the exact place where readability, testability, or change safety drops sharply.
4. If the complexity increase is material, use safe outputs to leave one concise comment pointing to the hotspot and the most realistic simplification path.
5. Prefer suggestions that reduce cognitive load, such as extraction, decomposition, clarified state flow, or splitting responsibilities.
6. If the code is dense but still coherent, say that explicitly instead of manufacturing a complaint.
7. Focus on review and maintenance risk, not stylistic preferences.

## Expected Output
- A focused complexity finding tied to the most difficult part of the changed logic.
- Clear explanation of how the current shape raises regression or review risk.

## Customization Notes
- Add repository-specific thresholds for acceptable complexity or known hotspot modules.
- If your team prefers small refactor suggestions, keep the output framed around the smallest safe simplification.
- Keep comments limited to the highest-risk complexity increase in the diff.
