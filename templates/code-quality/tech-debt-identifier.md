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

# Tech Debt Identifier

## Purpose
Identify technical debt introduced or exposed by the current change before it becomes normalized in the codebase.

## Trigger
Run when a pull request adds shortcuts, compatibility shims, repeated logic, temporary flags, or known compromises that may survive longer than intended.

## Instructions
1. Inspect the change for signs of debt such as duplicated logic, temporary conditionals, bypasses, special cases, missing cleanup after migrations, or code intentionally marked as a short-term compromise.
2. Distinguish necessary pragmatic tradeoffs from debt that is likely to create repeated maintenance cost.
3. Prioritize debt that affects future feature work, testing complexity, reliability, or code ownership.
4. If meaningful debt is introduced or exposed, use safe outputs to leave one concise comment naming the debt shape and the likely long-term cost.
5. When useful, suggest the smallest follow-up cleanup that would keep the debt from hardening.
6. Avoid calling every imperfect tradeoff "tech debt" when the compromise is proportionate and well-contained.
7. Focus on durable maintenance burden, not abstract code purity.

## Expected Output
- A focused technical-debt finding tied to a concrete compromise in the diff.
- Clear explanation of the likely maintenance cost if the compromise remains in place.

## Customization Notes
- Add repository-specific examples of acceptable temporary fixes versus debt that should be called out immediately.
- If your team tracks debt labels or follow-up issues, align the wording with that workflow.
- Keep comments limited to the few compromises most likely to create future drag.
