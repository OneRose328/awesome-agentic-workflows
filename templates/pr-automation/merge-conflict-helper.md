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

# Merge Conflict Helper

## Purpose
Surface the most likely merge-conflict hotspots and give reviewers a short recovery plan before the branch drifts further.

## Trigger
Run when a pull request is updated after a long review cycle, touches shared hotspots, or is marked ready for review with a non-trivial chance of merge pain.

## Instructions
1. Scan the changed files and identify overlap with common conflict zones such as lockfiles, shared config, route maps, schema definitions, generated manifests, and central exports.
2. Call out files that are both high-churn and structurally sensitive, where line-order or dependency updates frequently collide.
3. Distinguish between likely textual conflicts, likely semantic conflicts, and low-risk overlaps that only look noisy.
4. Use safe outputs to leave one review comment that names the top conflict hotspots and the branch areas maintainers should rebase against first.
5. When useful, suggest a conflict-reduction sequence such as rebasing after dependency updates, splitting generated files, or landing schema changes before consumer updates.
6. If the risk is low, say so explicitly so reviewers do not waste time on false alarms.
7. If confidence is weak because the branch context is missing, state the uncertainty instead of inventing conflicts.

## Expected Output
- A ranked list of likely conflict hotspots with a short explanation of why they are risky.
- One actionable rebase or merge-order recommendation that reduces review churn.

## Customization Notes
- Add repository-specific hotspot paths such as generated API clients, monorepo lockfiles, or deployment manifests.
- Adjust the comment style to match whether your team prefers author guidance, reviewer guidance, or release-manager notes.
- Keep outputs limited to the highest-risk files so the workflow stays high-signal.
