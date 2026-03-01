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

# Test Coverage Reminder

## Purpose
Flag pull requests that appear to change behavior without enough accompanying test coverage.

## Trigger
Run when a pull request changes business logic, edge-case handling, or public behavior and reviewers need a fast test-gap check.

## Instructions
1. Compare the changed production code against the changed test files and identify whether the behavioral surface expanded, shifted, or tightened.
2. Focus on risky areas: branching logic, validation rules, serializers, permission checks, migrations, parsing, caching, and regressions around bug fixes.
3. Distinguish between changes that truly need new tests and refactors that are likely test-neutral.
4. If coverage appears thin, point to the exact behavior that should be asserted rather than vaguely requesting "more tests."
5. Use safe outputs to leave one concise review comment that highlights the main missing test scenario or confirms coverage looks proportionate.
6. If the repository already has strong end-to-end or snapshot coverage that plausibly covers the change, note that instead of over-reporting.
7. If the diff is too large for a confident coverage read, say so and name the riskiest area to inspect manually.

## Expected Output
- A high-signal note on whether the changed behavior appears under-tested.
- One concrete testing suggestion that a contributor can act on immediately.

## Customization Notes
- Add repository-specific expectations for unit, integration, contract, or end-to-end coverage.
- Tune the reminder style to match whether your team prefers reviewer comments or maintainer nudge notes.
- Keep the output limited to the highest-value missing scenario, not an exhaustive test plan.
