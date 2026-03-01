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

# Retrospective Helper

## Purpose
Prepare a retrospective summary that turns recent work into actionable wins, pain points, and next-step improvements.

## Trigger
Run after a sprint, release cycle, or incident recovery window when the team needs a structured retro draft.

## Instructions
1. Review recent issues, pull requests, release notes, and visible workflow friction to identify what materially affected the team's execution.
2. Separate clear wins from recurring pain points, and distinguish process issues from one-off anomalies.
3. Prioritize observations that can lead to concrete process changes, not vague morale commentary.
4. Use safe outputs to create one issue that groups findings into wins, pain points, and a short list of follow-up actions.
5. If the repository evidence is incomplete, note the blind spots instead of pretending the retro is comprehensive.
6. Keep the output neutral and specific so the team can reuse it in an actual retro meeting.
7. Prefer a few actionable follow-ups over a long complaint list.

## Expected Output
- A meeting-ready retrospective draft that saves the team preparation time.
- A short set of concrete follow-up actions tied to observed repository activity.

## Customization Notes
- Add your real sprint cadence, retro categories, and decision format.
- If your team tracks action items elsewhere, align the issue format with that system.
- Keep the output focused on decisions the team can actually change next cycle.
