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

# Onboarding Guide

## Purpose
Create a step-by-step onboarding checklist that gets a new contributor from fresh clone to first safe contribution.

## Trigger
Run when maintainers want a fresh onboarding checklist or when setup docs have materially changed.

## Instructions
1. Read the repository setup docs, contribution guide, scripts, and any example workflows a new contributor is expected to run first.
2. Build a practical onboarding path in the order a newcomer would actually need it: prerequisites, environment setup, validation, project orientation, and first safe contribution.
3. Keep the checklist concrete. Prefer “run X, confirm Y, then open Z file” over vague advice like “understand the codebase”.
4. Flag hidden prerequisites such as required API keys, CLI tools, local services, access approvals, or platform assumptions if they appear in the docs.
5. Separate the true first-success path from optional deeper setup so newcomers can get unblocked quickly.
6. Use safe outputs to publish a single checklist issue or onboarding note that maintainers can link newcomers to.
7. If repository docs are incomplete or contradictory, call out the gap instead of pretending the onboarding path is already clean.

## Expected Output
- A concrete onboarding checklist that shortens time to first successful setup.
- Explicit callouts for missing docs, hidden prerequisites, or ambiguous first steps.

## Customization Notes
- Add your preferred newcomer path, such as “docs-only first PR” or “run example workflow before coding”.
- If your project has multiple setup modes, tell the workflow which one should be the default onboarding route.
- If the project has privileged or maintainer-only steps, mark those as optional or out of scope for newcomers.
- Keep the checklist scoped to first success, not full project mastery.
