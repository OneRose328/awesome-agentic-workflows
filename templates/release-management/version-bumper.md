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

# Version Bumper

## Purpose
Recommend the next version bump based on visible release impact, compatibility changes, and the repository's actual versioning rules.

## Trigger
Run when maintainers are deciding whether the next release should be a patch, minor, or major version.

## Instructions
1. Review the release scope, merged pull requests, breaking changes, new features, bug fixes, and any versioning notes already present.
2. Classify the release impact in semantic-version terms: patch for compatible fixes, minor for backward-compatible features, major for breaking changes or compatibility resets.
3. Prefer the highest-impact justified change in the release window, but cite the exact changes that triggered that recommendation.
4. Distinguish code changes that are technically large from changes that are actually version-significant for downstream users.
5. If versioning is ambiguous because the release boundary is unclear or migration impact is unknown, explain exactly what must be confirmed before choosing the bump.
6. Use safe outputs to create or refresh one version recommendation artifact that includes the proposed next version, the deciding changes, and any uncertainty.
7. Keep the recommendation practical and short. Maintainers should be able to accept or reject it quickly.
8. Do not invent semantic-version rigor for repositories that clearly use a different release convention; instead, call out the mismatch and defer to the project rule.

## Expected Output
- A clear version bump recommendation tied to visible release impact and compatibility expectations.
- Enough reasoning for maintainers to defend the version choice without rereading the full release window.

## Customization Notes
- Add your repository's real versioning policy if it differs from standard semantic versioning.
- If you version by channel, branch, or train, define how the workflow should resolve that before choosing a bump.
- If your project uses release trains or calendar versions, redefine the decision rule so the workflow reflects that reality.
- Keep the output to one canonical recommendation so version decisions stay centralized.
