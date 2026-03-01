---
on:
  issues:
    types: [opened, edited]
permissions:
  issues: read
tools:
  github:
    toolsets: [issues, labels]
network: defaults
safe-outputs:
  add-comment:
    max: 1
  update-issue:
---

# Stale Issue Closer

## Purpose
Finds inactive issues and proposes a structured stale workflow.

## Trigger
Run when an open issue has gone quiet long enough that it may be blocking queue hygiene without active maintainer value.

## Instructions
1. Review the issue age, last maintainer reply, last contributor reply, open blockers, and whether the thread still contains actionable information.
2. Distinguish truly stale issues from slow-moving but still valid work such as long-lived bugs, accepted feature requests, or roadmap-tied tasks.
3. If the issue is stale, use safe outputs to leave one clear comment that explains the inactivity threshold, what updated information is needed, and how the reporter can revive the thread.
4. Use issue updates only for lightweight stale-state tracking that matches the repository policy; do not close issues by default unless the project explicitly wants that behavior.
5. If the issue involves security, data loss, or a still-reproducible production problem, do not treat silence alone as a reason to stale it.
6. Keep the workflow focused on queue hygiene, not on re-triaging the full issue.
7. When in doubt, prefer a gentle stale warning over an aggressive cleanup action.

## Expected Output
- A consistent stale-process action that reduces backlog clutter without discarding still-relevant reports.
- A clear path for the reporter to re-engage with updated context.

## Customization Notes
- Define your inactivity threshold and whether the workflow should warn, label, or close.
- If your repository reopens stale issues automatically when the reporter replies, mention that policy explicitly.
- Keep cleanup conservative for high-severity or long-lived known issues.
