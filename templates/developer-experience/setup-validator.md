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
  add-comment:
    max: 1
---

# Setup Validator

## Purpose
Check whether a fresh contributor can still follow the documented setup path without avoidable confusion or hidden blockers.

## Trigger
Run when setup docs, bootstrap scripts, dependency versions, or onboarding paths change enough that the local setup experience may have drifted.

## Instructions
1. Read the setup guide, contribution guide, bootstrap scripts, package manager files, and the first commands a new contributor is expected to run.
2. Look for real onboarding drift: renamed commands, missing prerequisites, hidden environment variables, platform assumptions, outdated version requirements, or steps that now depend on removed files.
3. Focus on the earliest point a fresh clone would fail or become confused. Early blockers matter more than late polish.
4. Identify the smallest change that would unblock the next contributor: one missing prerequisite, one renamed command, one missing file reference, or one undocumented branch in the setup path.
5. Use safe outputs to leave one concise validation note or remediation comment rather than a scattered list of minor style nits.
6. If repository evidence cannot confirm a step, mark it as unverified instead of calling it correct or broken with false confidence.
7. Prefer setup reliability over documentation style. The question is whether someone can get working, not whether the prose is elegant.

## Expected Output
- A focused setup reliability result that identifies the first-time contributor blockers most likely to matter.
- Clear separation between confirmed drift, likely drift, and unverified assumptions.

## Customization Notes
- Add the exact bootstrap commands your project treats as the success path.
- If your team supports multiple platforms, state which platform should be validated by default.
- Keep the output short and action-oriented so maintainers can fix setup drift quickly.
