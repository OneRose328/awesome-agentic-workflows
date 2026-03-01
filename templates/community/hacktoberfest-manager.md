---
on:
  workflow_dispatch: {}
permissions:
  issues: read
  discussions: read
tools:
  github:
    toolsets: [issues, discussions]
network: defaults
safe-outputs:
  add-comment:
    max: 1
---

# Hacktoberfest Manager

## Purpose
Prepare and curate contribution opportunities for seasonal events such as Hacktoberfest without flooding maintainers with manual sorting.

## Trigger
Run when maintainers are preparing a contributor event window and need a quick review of which issues are suitable to surface.

## Instructions
1. Review open issues and identify tasks that are bounded, beginner-friendly, non-sensitive, and unlikely to block core release work.
2. Filter out stale, underspecified, or high-context issues that would frustrate event contributors.
3. Prefer issues with clear acceptance criteria, visible ownership, and low coordination overhead.
4. Use safe outputs to post one short comment that flags the best candidate issues or notes why no current issues are event-ready.
5. If an issue needs cleanup before it can be exposed to new contributors, say what is missing.
6. Avoid surfacing security-sensitive, architecture-heavy, or urgent production issues as event tasks.
7. Keep recommendations practical for maintainers who need to curate a small set of welcoming entry points.

## Expected Output
- A short list of contribution-ready issues or a clear note that the current backlog is not ready.
- Better curation signal for seasonal contributor programs.

## Customization Notes
- Replace event wording with your actual community program, seasonal campaign, or newcomer initiative.
- Add your repository's rules for what qualifies as beginner-friendly and safe for external contributors.
- Keep the recommendations small and maintainable so event curation stays realistic.
