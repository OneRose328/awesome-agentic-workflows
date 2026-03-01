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

# Beta Feedback Collector

## Purpose
Cluster beta feedback into release blockers, repeated themes, and follow-up items that need ownership before general availability.

## Trigger
Run when a beta release is collecting user feedback and release owners need a structured summary instead of a raw issue stream.

## Instructions
1. Review the issues, PR references, and notes tied to the current beta window, focusing on externally reported defects, usability friction, and upgrade confusion.
2. Separate urgent release blockers from non-blocking polish so release owners can prioritize the next decision.
3. Group repeated feedback into a few themes, such as onboarding pain, regressions, docs gaps, performance issues, or missing migration guidance.
4. Highlight feedback that appears anecdotal or low-confidence so it is not over-weighted.
5. Use safe outputs to create one issue that captures the beta summary, top blockers, and explicit next-step owners or lanes.
6. Keep the summary focused on what changes release readiness, not a full digest of every comment.
7. If the beta scope is unclear, state which release version or time window needs to be defined first.

## Expected Output
- A release-readiness summary that separates blockers from general feedback.
- A reusable artifact that helps maintainers decide whether to extend, patch, or ship the beta.

## Customization Notes
- Add your real beta channels, issue labels, and severity thresholds for what counts as a ship blocker.
- If your team uses fixed checkpoints, include explicit decision buckets such as extend beta, patch before GA, or accept known issue.
- Keep the output in one canonical summary issue so discussion stays centralized.
