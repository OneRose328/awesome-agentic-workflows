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

# Dependency Update Summary

## Purpose
Summarize dependency upgrades for a release window and call out the upgrades most likely to change runtime behavior, security posture, or release safety.

## Trigger
Run when a release includes multiple dependency bumps and maintainers need a risk-focused summary before shipping.

## Instructions
1. Review the dependency-related pull requests and identify which libraries, runtimes, SDKs, or tooling versions changed in the current release slice.
2. Separate routine low-risk bumps from upgrades that alter compatibility or operational risk, such as major versions, framework shifts, auth libraries, database clients, compilers, or build tooling.
3. Highlight the changes most likely to require focused verification: runtime behavior changes, migration notes, integration retests, or rollback attention.
4. Ignore low-signal churn when the dependency bump is trivial and unlikely to affect users or maintainers.
5. Use safe outputs to create one issue that summarizes only the dependency changes that can affect release confidence.
6. Structure the output around three questions: what changed, what might break, and what still needs verification.
7. If the dependency scope is unclear, state which pull requests, manifests, or lockfile changes must be reviewed before a reliable summary is possible.

## Expected Output
- A release-facing dependency summary that tells maintainers where to spend verification time before shipping.
- One concise artifact that centralizes the upgrades most likely to affect release safety.

## Customization Notes
- Add repository-specific rules for what counts as high-risk dependencies and which teams own them.
- If your project tracks upgrade verification checklists, link the summary style to those checkpoints.
- Keep the summary short enough to use in a real release review meeting.
