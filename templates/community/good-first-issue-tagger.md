---
on:
  issues:
    types: [opened, edited]
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

# Good First Issue Tagger

## Purpose
Identify issues that are realistic, low-risk entry points for first-time contributors.

## Trigger
Run when maintainers want a quick check on whether an issue can be safely marked as a beginner-friendly task.

## Instructions
1. Read the issue and decide whether the task is bounded, well-defined, and safe for a new contributor to attempt.
2. Check whether the issue has clear acceptance criteria, manageable scope, and enough context to avoid maintainer hand-holding.
3. Reject issues that are urgent, security-sensitive, architecture-heavy, or deeply coupled to internal context.
4. Use safe outputs to leave one short comment indicating whether the issue appears suitable for a `good first issue` label and why.
5. If the issue is close but not ready, name the missing detail that would make it contributor-friendly.
6. Prefer conservative tagging over optimistic tagging that leads to contributor churn.
7. Keep the guidance practical for maintainers who need a trustworthy filter.

## Expected Output
- A reliable signal on whether an issue is truly newcomer-friendly.
- One concise rationale that helps maintainers label or refine the issue.

## Customization Notes
- Replace the suitability criteria with your repository's actual expectations for beginner issues.
- Add explicit exclusions for areas where newcomers should not start, such as release tooling or security work.
- Keep recommendations conservative so the label remains trustworthy.
