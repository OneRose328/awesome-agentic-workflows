---
on:
  workflow_dispatch: {}
permissions:
  contents: read
  issues: read
  pull-requests: read
tools:
  github:
    toolsets: [repos, pull_requests, issues]
network: defaults
safe-outputs:
  create-issue:
    max: 1
---

# Release Checklist

## Purpose
Build a release-owner checklist that reflects the actual state of the repository, not a generic ship template.

## Trigger
Run when a release owner is preparing a release candidate, final release, or hotfix transition.

## Instructions
1. Review the intended release scope, merged pull requests, outstanding blockers, release note state, and any visible CI, packaging, or deployment signals.
2. Build a checklist around actual release gates: green verification, version and changelog readiness, migration communication, dependency risk review, and rollback confidence.
3. Mark each line as ready, blocked, or unknown based on repository evidence. Never imply an item is complete if the signal is missing.
4. Call out the blockers that matter most in a real release window: failing checks, missing release notes, unresolved breaking changes, incomplete migrations, or unreviewed hotfixes.
5. Keep the checklist tight enough that a release owner could use it live during a ship decision.
6. Use safe outputs to create or refresh one release-tracking issue that can serve as the canonical preparation list.
7. If the release boundary is unclear, explicitly say what must be confirmed before the checklist can be trusted.

## Expected Output
- One release checklist a human could actually drive a ship or no-ship call from.
- Clear separation between ready items, release blockers, and unknowns that still need verification.

## Customization Notes
- Replace the example release gates with your actual ship criteria.
- If you have separate stable, beta, and hotfix paths, define which checklist variant should be used for each.
- Keep `safe-outputs.create-issue.max` at `1` so the team has one canonical release checklist per run.
