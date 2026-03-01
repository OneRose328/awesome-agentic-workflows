---
on:
  workflow_dispatch: {}
permissions:
  contents: read
  issues: read
tools:
  github:
    toolsets: [repos, issues]
network: defaults
safe-outputs:
  create-issue:
    max: 1
---

# Sprint Planner

## Purpose
Build a draft sprint scope from the current backlog, visible dependencies, and maintenance pressure.

## Trigger
Run before sprint planning or whenever maintainers want a current proposal for the next focused work window.

## Instructions
1. Review the backlog for work that is ready, blocked, partially in progress, or tied to urgent support and release commitments.
2. Draft a realistic sprint scope using only work with enough clarity to start, while accounting for visible dependencies, unresolved blockers, and maintenance load.
3. Separate must-do items from stretch items so the proposal can survive real-world interruptions and urgent support work.
4. Flag work that should not enter the sprint yet because it is underspecified, blocked by another team, or likely too large for one cycle.
5. Use safe outputs to publish one planning draft that groups proposed work by priority, dependency risk, and readiness.
6. If capacity assumptions are missing, make that explicit instead of pretending the scope is final.
7. Prefer a plan that is slightly conservative over a plan that collapses as soon as one dependency slips.
8. Keep the result useful for a planning meeting: practical, constrained, and easy to debate.

## Expected Output
- A draft sprint plan that gives maintainers a credible starting point instead of a raw issue list.
- Clear distinction between committed work, stretch work, and work that should stay out of scope.

## Customization Notes
- Define what “ready” means in your team so the planner does not pull in ambiguous backlog items.
- If you run fixed-length sprints, note the expected cycle length and capacity assumptions.
- If your team reserves explicit capacity for bugs or interrupts, encode that constraint here.
- Keep the planning output in one canonical issue or planning note so discussion stays centralized.
