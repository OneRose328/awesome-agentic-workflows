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

# PR Size Checker

## Purpose
Warn when a pull request is large enough to create review risk, merge risk, or delayed feedback loops.

## Trigger
Run when a pull request is opened or updated and maintainers want a fast check on whether the scope is review-safe.

## Instructions
1. Assess the pull request size using the changed files, likely review surface, and whether the diff mixes unrelated concerns.
2. Distinguish between mechanically large but low-risk changes and logically dense changes that are hard to review even if line count is moderate.
3. Flag risk factors such as mixed refactor plus feature work, broad cross-cutting edits, generated files hiding logic changes, or missing decomposition.
4. If the pull request appears too large, suggest the most realistic split strategy, such as separating refactors, generated artifacts, docs, or follow-up cleanup.
5. Use safe outputs to leave one concise comment that states whether the size is acceptable and, if not, why review risk is elevated.
6. If the change is large but still coherent, say so explicitly to avoid false alarms.
7. Keep the recommendation proportional; do not demand splitting changes that are already near merge and internally consistent.

## Expected Output
- A clear signal on whether the pull request size is likely to slow or degrade review quality.
- One practical recommendation to reduce review risk when the PR is too broad.

## Customization Notes
- Add your repository's real thresholds for acceptable PR size or review slices.
- If generated files are common, teach the workflow which paths should count less toward review risk.
- Keep the output focused on reviewability, not vanity metrics.
