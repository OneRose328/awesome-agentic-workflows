---
on:
  workflow_dispatch: {}
permissions:
  contents: read
  issues: read
tools:
  github:
    toolsets: [repos, issues]
network: defaults
safe-outputs:
  create-issue:
    max: 1
---

# Standup Generator

## Purpose
Creates a short standup summary from recent progress and blockers.

## Trigger
Run when the team needs a quick daily or periodic status snapshot without manually gathering every update.

## Instructions
1. Review recent pull requests, issue movement, blockers, and any visible signs of in-progress work relevant to the current standup window.
2. Summarize updates in a practical standup shape: recent progress, current blockers, and likely next actions.
3. Keep the summary short enough to read aloud in a real standup or scan asynchronously in under a minute.
4. Highlight blockers and transition risks more than routine activity, since those are the updates most likely to change the team's plan.
5. Use safe outputs to create one concise standup note or issue update.
6. If the repository activity is too sparse to infer real progress, say so instead of fabricating status.
7. Avoid status theater. Prefer useful operational signal over inflated summaries.

## Expected Output
- A concise standup summary that reduces manual status collection.
- Clear visibility into blockers, recent movement, and likely next work.

## Customization Notes
- Define the reporting window and standup format your team actually uses.
- If your team prefers async standups, tune the output for quick text scanning rather than spoken updates.
- Keep the output in one predictable location so the team knows where to look each cycle.
