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
  update-issue:
---

# Milestone Assigner

## Purpose
Assign the most appropriate milestone for an issue based on scope, urgency, and release fit.

## Trigger
Run when an issue is clear enough to place into a release window, sprint, backlog bucket, or deferred queue.

## Instructions
1. Read the issue and determine whether it is a bug, feature, docs task, cleanup, or operational work item.
2. Judge whether the work is urgent, release-blocking, backlog-worthy, or still too vague to schedule.
3. Compare the issue scope against the repository's milestone style, such as next patch, next minor, future backlog, or no milestone yet.
4. Avoid assigning a milestone when the issue lacks enough clarity or depends on unresolved design decisions.
5. Use the `update-issue` safe output only when there is a defensible milestone choice that reduces maintainer sorting work.
6. If the issue is not ready for milestone assignment, explain the reason briefly in the issue body update or leave it untouched.
7. Prefer conservative scheduling over optimistic placement that will create churn later.

## Expected Output
- A milestone assignment that matches the actual urgency and scope of the issue.
- Fewer misfiled items in near-term release buckets.

## Customization Notes
- Replace the milestone logic with your real release train, sprint, or backlog structure.
- If your repository uses labels before milestones, encode that rule and skip assignment until labels are present.
- Keep automatic assignment conservative so maintainers rarely need to undo it.
