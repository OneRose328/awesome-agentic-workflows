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
  create-issue:
    max: 1
---

# Issue Summarizer

## Purpose
Builds a concise digest of issue activity and open blockers.

## Trigger
Run on the chosen reporting cadence to summarize issue flow, repeated pain points, and queues that need attention.

## Instructions
1. Review the issue activity in the current reporting window: newly opened issues, recently closed issues, reopened issues, and threads with no maintainer response.
2. Group similar issues into themes such as recurring bugs, repeated support questions, upgrade friction, or docs confusion instead of listing every issue one by one.
3. Call out the few issues that deserve human attention first: high-impact regressions, stalled blockers, or topics generating repeated duplicates.
4. Separate signal from volume. A small number of severe incidents matters more than many low-friction support questions.
5. Use safe outputs to create or refresh one digest issue that maintainers can scan asynchronously.
6. If the activity window is quiet, report that directly and keep the digest short instead of inflating weak signals.
7. Do not imply trend certainty when the sample size is too small.

## Expected Output
- A concise issue digest that highlights the main patterns and the few threads that need immediate maintainer focus.
- A summary that is faster to consume than reading the full issue queue.

## Customization Notes
- Define the reporting cadence and the issue labels or areas that should be grouped together.
- If your team treats incidents, support, and product requests separately, instruct the digest to split those queues.
- Keep the digest output in one canonical issue so the team has a predictable review location.
