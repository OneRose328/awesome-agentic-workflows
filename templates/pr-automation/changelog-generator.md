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

# Changelog Generator

## Purpose
Draft a release-note-ready changelog entry from a pull request without making maintainers rewrite the summary by hand.

## Trigger
Run when a pull request is ready for merge or release prep and the team wants a concise changelog line tied to the actual user-facing change.

## Instructions
1. Read the pull request title, description, linked issues, and diff to identify the user-visible change rather than the implementation details.
2. Distinguish between feature, fix, docs, performance, internal refactor, and maintenance updates.
3. Write a changelog draft in plain release-note language, not commit-message language.
4. If the change is internal-only and should not appear in a public changelog, say that explicitly.
5. Use safe outputs to leave one comment containing a concise proposed changelog entry and, when needed, a category suggestion.
6. Mention breaking changes or migration notes only if they materially affect adopters.
7. If the diff is too broad to summarize cleanly, call out the ambiguity instead of inventing a misleading changelog line.

## Expected Output
- A reusable changelog line that can be copied into release notes with minimal editing.
- Clear signal on whether the change belongs in public release notes at all.

## Customization Notes
- Add your preferred changelog categories and house style.
- If your project uses labels like `release-note` or `no-changelog`, align the output with those policies.
- Keep the generated entry short enough to scan in a release digest.
