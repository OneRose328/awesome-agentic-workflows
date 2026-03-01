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

# Roadmap Updater

## Purpose
Summarize repository signals that should influence roadmap communication, prioritization, or public roadmap adjustments.

## Trigger
Run on a schedule when maintainers want a lightweight roadmap pulse from recent issues, discussions, and recurring requests.

## Instructions
1. Review recent issues and discussions for repeated asks, persistent pain points, and topics that have gained momentum.
2. Separate roadmap-relevant signals from one-off support questions or low-signal complaints.
3. Identify themes that may warrant roadmap visibility, de-prioritization, clearer messaging, or explicit "not planned" communication.
4. Use safe outputs to create one issue summarizing the top roadmap-relevant themes and the likely action each theme suggests.
5. Keep the summary focused on decision signal, not community chatter volume.
6. If the evidence is thin or contradictory, say so clearly instead of forcing a roadmap conclusion.
7. Avoid implying commitments that maintainers have not actually made.

## Expected Output
- A roadmap-facing summary that helps maintainers decide what deserves communication or prioritization.
- One reusable planning artifact that captures the strongest community signals.

## Customization Notes
- Replace the cadence and labels with your real planning rhythm and roadmap process.
- Add repository-specific thresholds for what counts as a meaningful theme versus isolated feedback.
- Keep the summary anchored to evidence so it remains useful in planning discussions.
