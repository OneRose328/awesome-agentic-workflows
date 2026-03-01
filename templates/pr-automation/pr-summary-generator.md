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

# PR Summary Generator

## Purpose
Creates a structured summary for reviewers before full review starts.

## Trigger
Run when a pull request is opened, substantially updated, or marked ready for review and the reviewer needs a fast orientation pass.

## Instructions
1. Read the pull request title, description, linked issues, changed files, and visible test or check results.
2. Summarize the change in reviewer-first language: what changed, why it changed, where the risk is, and what kind of review is needed first.
3. Group the summary into a practical shape such as Intent, Main Change Areas, Risk Surface, Testing Signals, and Follow-up Questions when those sections are useful.
4. Highlight behavior changes, migrations, schema changes, config changes, or docs impact explicitly instead of burying them in a file list.
5. If the pull request is oversized or poorly described, say so directly and point reviewers to the areas that matter most.
6. Use safe outputs to post one concise summary comment that helps the next reviewer start quickly.
7. Do not restate the diff mechanically. Prefer synthesis over a raw file inventory.

## Expected Output
- A compact summary that lets reviewers understand scope, risk, and likely review order in under a minute.
- Clear signal about whether the pull request is straightforward, risky, or under-documented.

## Customization Notes
- Add any project-specific sections you expect in pull request summaries, such as rollout plan, data migration, or release-note impact.
- Keep this workflow to one summary comment so it complements, rather than replaces, human review.
- If your repository already enforces a rich PR template, make this workflow fill gaps rather than duplicate the template.
