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

# Hotfix Coordinator

## Purpose
Keep an urgent hotfix release aligned on the minimum safe path to patch production without dragging in non-essential change.

## Trigger
Run when a production fix, security patch, or urgent regression needs a fast but controlled release path.

## Instructions
1. Review the hotfix trigger: active incident, production regression, broken release, or urgent security exposure.
2. Identify the minimum safe path to ship: required code fix, review owners, validation gates, rollback plan, and any backport or patch branch requirement.
3. Separate critical-path work from non-blocking cleanup, follow-up refactors, and nice-to-have fixes. A hotfix should move fast, but only on steps that directly affect safe release.
4. Call out anything that would make the hotfix unsafe to rush, such as missing reproduction, unreviewed high-risk changes, unclear blast radius, or no rollback strategy.
5. Use safe outputs to create or refresh one hotfix tracking issue with the current status, blockers, owners, and next actions.
6. Keep the output operational and time-sensitive. This is not a normal release plan and should not read like one.
7. If the incident severity is unclear, state the uncertainty and avoid over-escalating routine fixes into hotfix mode.
8. Prefer the smallest reversible path that restores service or risk posture first.

## Expected Output
- A clear hotfix action path that helps maintainers move quickly without skipping release-critical safeguards.
- One current source of truth for blockers, approvals, ownership, and deployment readiness.

## Customization Notes
- Add your actual hotfix branch naming, approval rules, and rollback expectations.
- If your project uses severity levels, define which levels should trigger this workflow.
- If your team uses incident roles, specify how those roles should map into the hotfix plan.
- Keep the output centralized in one tracking issue so responders are not splitting status across threads.
