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

# Release Announcement

## Purpose
Draft a public-facing release announcement that turns finalized release notes into a concise, user-readable launch message.

## Trigger
Run when a release is approved and maintainers need a first-pass announcement for GitHub Releases, the changelog, or a community post.

## Instructions
1. Review the finalized release notes, version number, standout pull requests, and any breaking changes, deprecations, or migration steps that affect adoption.
2. Lead with the handful of changes users will care about most, not a change-by-change dump.
3. Separate the message into three layers: headline improvements, operator or maintainer-impacting changes, and upgrade cautions that must be seen before rollout.
4. Write for external readers. Avoid commit-log wording, internal release shorthand, or implementation trivia that does not help adoption.
5. Mention upgrade warnings only when they materially change how or whether someone should update.
6. Use safe outputs to create one draft issue that acts as the canonical announcement draft for human editing and distribution.
7. Keep the draft reusable across GitHub Releases, community posts, and lightweight social sharing with minimal trimming.
8. If the release scope is still unstable, say the announcement is not ready and name the missing release inputs.

## Expected Output
- A communication-ready launch draft with a clear lead, a few strong highlights, and only the upgrade cautions that matter.
- One draft that shortens release communications work instead of creating another long edit pass.

## Customization Notes
- Add your preferred release voice, formatting, and distribution targets such as GitHub Releases, Discord, or a blog.
- Insert repository-specific sections for migration notes, acknowledgements, or known issues if your audience expects them.
- Keep the generated draft in one canonical place so release owners edit a single source of truth.
