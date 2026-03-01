---
on:
  workflow_dispatch: {}
permissions:
  contents: read
  issues: read
  pull-requests: read
tools:
  github:
    toolsets: [repos, pull_requests, issues]
network: defaults
safe-outputs:
  create-issue:
    max: 1
---

# Release Digest

Prepare a compact release snapshot before a release owner ships.

## Instructions

1. Review recent merges and open release blockers.
2. Separate user-facing highlights from internal noise.
3. Summarize blockers that still need attention.
4. Use safe outputs to open or refresh one tracking issue containing the release digest.
5. Keep the final output concise enough for a go or no-go review.

## Notes

- Add your release branch naming and approval rules.
- If you prefer comments instead of issues, swap `create-issue` for `add-comment`.

