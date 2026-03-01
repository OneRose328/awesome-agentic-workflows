---
on:
  schedule: weekly
permissions:
  issues: read
  discussions: read
tools:
  github:
    toolsets: [issues, discussions]
network: defaults
safe-outputs:
  create-issue:
    max: 1
---

# Community Health Report

## Purpose
Summarizes response health, contribution flow, and support load so maintainers can spot drift before it becomes backlog drag.

## Trigger
Run on the configured recurring schedule to produce a compact community operations snapshot.

## Instructions
1. Review recent issue, pull request, and discussion activity within the current reporting window.
2. Summarize the signals that matter most to maintainers: new issue volume, unanswered threads, average response lag, contributor participation, reopened work, and any queue that is visibly backing up.
3. Highlight trends, not raw noise. Prefer “bug reports doubled this week and support threads are slowing review” over a long list of links.
4. Separate healthy growth from warning signs such as rising unanswered questions, repeated setup confusion, review bottlenecks, or one maintainer handling most public responses.
5. Distinguish short-lived spikes from sustained patterns so the team does not overreact to one busy day.
6. Use safe outputs to create one tracking issue or status post that maintainers can review asynchronously.
7. If the data is too thin to infer a trend, report only the observable facts and avoid overinterpreting small samples.

## Expected Output
- A short community health report that is useful for weekly or monthly maintainer review.
- A clear list of the few community signals that deserve action next, plus the likely operational pressure behind them.

## Customization Notes
- Define your reporting window explicitly if you want weekly, bi-weekly, or monthly summaries.
- Add any repository-specific health metrics you care about, such as first-response SLA or newcomer conversion.
- If your team has explicit support or review SLAs, map the report language to those thresholds.
- Keep the output to one canonical report so the team has a single place to review trends.
