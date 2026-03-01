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

# Breaking Change Detector

## Purpose
Flags contract or behavior changes that may break downstream users.

## Trigger
Run when a pull request touches public APIs, config defaults, schemas, protocols, or other user-visible contracts.

## Instructions
1. Inspect the changed interfaces, defaults, schemas, commands, and upgrade assumptions in the pull request.
2. Look for actual compatibility risk: removed fields, renamed flags, changed required inputs, default behavior shifts, incompatible schema changes, or altered auth and permission expectations.
3. Distinguish cosmetic refactors from user-facing contract breaks. If callers or operators would not notice, it is not a breaking change.
4. When a breaking change is likely, use safe outputs to leave one focused review comment describing what may break and what follow-up is needed: migration notes, version bump, deprecation notice, or release-note callout.
5. If the risk is uncertain, explain the missing context rather than labeling everything as breaking by default.
6. Prioritize clarity for downstream users and maintainers over exhaustive protocol theory.
7. Do not treat implementation churn as a breaking change unless it changes the observable contract.

## Expected Output
- A precise warning when a change is likely to break consumers, deployers, or integrators.
- Clear guidance on the minimum next step needed before merge.

## Customization Notes
- Add the exact interfaces your project treats as public contracts.
- If your release policy has a formal definition of “breaking”, encode that threshold here.
- Keep this workflow comment-light so it only fires when compatibility risk is real.
