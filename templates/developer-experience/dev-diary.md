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

# Dev Diary

## Purpose
Produce concise development notes from recent repository activity so maintainers can reconstruct progress without reading every thread.

## Trigger
Run when maintainers want a short working log for a sprint, milestone, or recent batch of repository activity.

## Instructions
1. Review recent issues, pull requests, and documentation changes to identify what actually moved forward.
2. Summarize progress in plain operational language: what changed, what is still blocked, and what likely comes next.
3. Favor signal over completeness; ignore low-value churn that does not change project state.
4. Use safe outputs to create one issue that captures the current progress snapshot as a compact working log.
5. If the repository evidence is incomplete, note the blind spots instead of pretending the summary is exhaustive.
6. Keep the diary useful for maintainers resuming work after a gap, not as a marketing update.
7. Highlight blockers and pending decisions more than routine edits.

## Expected Output
- A compact progress log that helps maintainers resume work quickly.
- A reusable summary of recent momentum, blockers, and likely next actions.

## Customization Notes
- Align the note format with your actual sprint log, weekly update, or internal project journal style.
- Add repository-specific sections if your team tracks blockers, owners, or release readiness explicitly.
- Keep the log concise enough that it remains cheaper to read than the raw activity feed.
