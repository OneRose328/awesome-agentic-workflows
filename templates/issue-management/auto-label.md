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
  add-labels:
    max: 3
  add-comment:
    max: 1
---

# Auto Label

## Purpose
Automatically applies an initial label set to a newly opened or updated issue.

## Trigger
Run when a new issue is opened or when an edited issue changes the category, subsystem, or severity implied by the report.

## Instructions
1. Read the issue title, body, chosen issue template, and any paths, component names, or keywords mentioned by the reporter.
2. Map the report to the smallest useful label set: one label for type, one for affected area, and optionally one for urgency.
3. Prefer labels grounded in explicit evidence such as stack traces, file paths, platform names, API names, or reproduction steps.
4. If two labels would conflict, choose the more actionable one and avoid guessing.
5. Use safe outputs to add labels only. Leave a comment only if the labeling decision is ambiguous enough that a maintainer should review it.
6. Never add novelty labels just because a phrase sounds similar. Bias toward no label instead of the wrong label.

## Expected Output
- A small, high-signal label set that makes the issue easier to route and search.
- No noisy or speculative labels.

## Customization Notes
- Replace the example label logic with your exact type, area, and severity labels.
- Keep the maximum label count low so the workflow does not create taxonomy clutter.
- If you use repository-specific issue forms, update the labeling rules to read those fields explicitly.
