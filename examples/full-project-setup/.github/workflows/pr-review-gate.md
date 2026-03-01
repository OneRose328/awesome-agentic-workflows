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

# PR Review Gate

Give reviewers a fast summary of the riskiest parts of a pull request.

## Instructions

1. Review the pull request description and diff.
2. Highlight correctness, testing, and documentation risk.
3. Keep feedback focused on the highest-signal issues.
4. Use safe outputs to add at most two concise review comments.
5. Stop short of broad rewrite advice unless the change is clearly unsafe.

## Notes

- Add repository-specific merge blockers and testing standards.
- Keep comments short so reviewers can scan them quickly.

