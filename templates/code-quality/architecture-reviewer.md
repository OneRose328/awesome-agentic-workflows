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

# Architecture Reviewer

## Purpose
Checks whether a change fits existing architecture and boundaries.

## Trigger
Run when a pull request changes core modules, introduces a new abstraction, or touches multiple architectural layers.

## Instructions
1. Read the pull request diff, affected modules, and any visible layering or ownership boundaries already present in the repository.
2. Look for architectural drift: business logic leaking into transport layers, duplicated orchestration, hidden coupling, misplaced dependencies, or new abstractions with no clear long-term role.
3. Separate true design risk from harmless local refactors. Do not block a change just because it introduces a new type or file.
4. If you find a risk, explain the specific boundary being crossed, why it increases maintenance cost, and the smallest architectural correction that would improve the change.
5. Use safe outputs only for concise, high-signal review comments. Prefer one strong architectural comment over many weak ones.
6. If the repository lacks enough context to judge the architecture confidently, say which assumption is missing instead of forcing a verdict.

## Expected Output
- A focused review note when the change introduces clear architectural debt or coupling risk.
- No generic “clean architecture” advice detached from the actual diff.

## Customization Notes
- Add the boundary rules your team actually uses, such as domain vs. infrastructure, API vs. service, or app vs. package layers.
- If your repository has known architectural hotspots, point the workflow at those paths explicitly.
- Keep this workflow comment-light so it only fires when the design concern is real.
