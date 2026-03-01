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

# Migration Guide Generator

## Purpose
Create a migration guide when a release introduces breaking behavior, compatibility shifts, or upgrade steps users cannot infer safely on their own.

## Trigger
Run when a release includes breaking behavior, version jumps, renamed interfaces, removed features, or upgrade steps that users must actively perform.

## Instructions
1. Review the release scope, breaking pull requests, deprecated features, changed defaults, removed APIs, and any known migration notes already present.
2. Identify what users must change before or during upgrade: config changes, renamed commands, schema migrations, data backfills, dependency prerequisites, or rollout sequencing.
3. Structure the guide in practical order: who is affected, prerequisites, required changes, sequencing, validation steps, and rollback notes if relevant.
4. Prefer concrete migration steps over prose. A maintainer should be able to hand the result to a user performing the upgrade.
5. Call out irreversible steps, downtime windows, compatibility breaks, or staged rollout requirements explicitly.
6. Distinguish mandatory steps from optional cleanup so users know what blocks a successful upgrade.
7. Use safe outputs to create one migration-guide draft issue or tracking artifact that can be refined into public documentation.
8. If the release boundary or breaking scope is incomplete, list the missing facts that block a trustworthy migration guide.

## Expected Output
- A step-by-step upgrade guide that users can actually follow during a breaking release.
- Clear notice of required changes, sequencing, validation steps, and major risk points.

## Customization Notes
- Add any mandatory release-note sections or compatibility promises your project makes.
- If your project supports staged migration paths, specify when to generate a minimal path versus a full migration guide.
- If your project supports multiple deployment topologies, define which migration path should be treated as the default.
- Keep this workflow scoped to one canonical draft so users do not end up with conflicting upgrade instructions.
