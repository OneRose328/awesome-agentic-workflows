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

# Auto Assign Reviewer

## Purpose
Recommend the most relevant reviewer lanes for a pull request based on changed surfaces, review risk, and likely ownership boundaries.

## Trigger
Run when a pull request is opened or updated and maintainers need a fast reviewer-routing suggestion before manual triage.

## Instructions
1. Cluster the changed files into reviewer lanes that reflect how real teams review: core product logic, infrastructure, docs, test coverage, build tooling, or security-sensitive surfaces.
2. Rank the lanes by review importance, not by file count. A small auth change may need stronger review than a large docs change.
3. Call out the single best primary reviewer lane first, then name any secondary lane only if the pull request clearly crosses boundaries.
4. If the pull request mixes unrelated domains, say that split review routing is safer than forcing one overloaded reviewer path.
5. Use safe outputs to leave one concise comment that explains the recommended routing in terms maintainers can act on immediately.
6. Explain why the recommended lane matters: domain ownership, deployment risk, interface impact, or user-facing behavior.
7. Do not invent usernames unless the repository has explicit mapping rules. Role-based routing is better than false precision.
8. Avoid generating a long reviewer list. The goal is to shorten the decision, not create another triage problem.

## Expected Output
- A high-signal reviewer routing note with one clear primary lane.
- Enough rationale for a maintainer to assign review without re-reading the whole diff first.

## Customization Notes
- Add your repository's CODEOWNERS patterns, team names, or file-to-owner mapping rules.
- If your team uses reviewer rotations, encode the rotation logic outside the model and keep this workflow focused on routing rationale.
- Keep comments compact so the assignment hint is faster to scan than the diff itself.
