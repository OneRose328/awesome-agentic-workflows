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

# Release Notes Generator

## Purpose
Builds polished release notes from the latest merge window.

## Trigger
Run when maintainers are preparing a release candidate, final release, or release-summary checkpoint.

## Instructions
1. Review the pull requests, issues, and merged changes that belong in the current release window.
2. Separate user-facing changes from internal refactors, dependency churn, and maintenance noise. Release notes should emphasize what users will notice.
3. Group the notes into practical sections such as Highlights, Fixes, Breaking Changes, Upgrade Notes, and Internal Changes when those sections are warranted.
4. For each item, describe the outcome for users, not just the implementation detail. Prefer concrete verbs like added, fixed, improved, deprecated, or removed.
5. If a change introduces migration work, configuration changes, or rollback risk, call it out explicitly.
6. Use safe outputs to create or refresh a single release-notes tracking issue or draft artifact. Keep the output easy to copy into a release page.
7. If the release window is unclear, summarize what is known and list the missing release boundary information instead of guessing.

## Expected Output
- A concise, publication-ready draft that maintainers can reuse for GitHub Releases, changelogs, or announcements.
- Clear separation between user-facing value and internal maintenance work.

## Customization Notes
- Add your preferred release-note sections and tone.
- If your repository uses milestone-based releases, tell the workflow exactly how to determine the release window.
- Keep `safe-outputs.create-issue.max` at `1` so this workflow produces one canonical draft instead of multiple competing notes.
