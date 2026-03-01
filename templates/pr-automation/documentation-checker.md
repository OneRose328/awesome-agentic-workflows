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

# Documentation Checker

## Purpose
Detect pull requests that change reader-facing behavior without matching documentation updates.

## Trigger
Run when a pull request changes commands, APIs, configuration, setup steps, user-visible behavior, or operational expectations.

## Instructions
1. Identify whether the pull request changes something a reader relies on: setup flow, CLI syntax, config defaults, API behavior, deployment assumptions, troubleshooting steps, or visible UX.
2. Separate true documentation impact from internal-only refactors. Do not create docs work for changes users will never notice.
3. Check whether the pull request already updates the most likely docs surface: `README`, docs pages, examples, migration notes, or inline help text.
4. If documentation is missing, point to the specific behavior change and the most likely file or section that should be updated.
5. Prefer one targeted request over a generic docs warning. The author should know exactly what drift was detected.
6. If the impact is uncertain, say that the docs impact is likely but unconfirmed, and explain what needs a human check.
7. Do not flood the thread with documentation nits. Focus on missing or stale guidance that would actually mislead users or contributors.

## Expected Output
- One targeted documentation reminder only when the pull request creates real reader-facing drift.
- Silence on internal-only changes that do not justify a docs requirement.

## Customization Notes
- Add the canonical documentation locations your project uses, such as `README`, docs pages, config reference, or migration notes.
- If your repository differentiates user docs from contributor docs, instruct the workflow to point at the right destination.
- Keep this workflow limited to one high-signal comment per pull request.
