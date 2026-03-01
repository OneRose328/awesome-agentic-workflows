# Contributing

This repository is meant to stay practical. New templates should solve a real repository problem, use current GitHub Agentic Workflows conventions, and be easy to adapt.

## Ground Rules

- Write templates in clear English.
- Prefer concrete actions over generic AI filler.
- Keep filenames in kebab-case.
- Re-check current GitHub Agentic Workflows docs before changing frontmatter conventions.
- Keep template bodies structured so reviewers can audit behavior quickly.

## Required Template Shape

Each template should include:

1. YAML frontmatter wrapped in `---`
2. `on`, `permissions`, and `tools` keys
3. `network: defaults`
4. `safe-outputs` when the workflow needs to create comments, labels, issues, or other write actions
5. A Markdown title
6. `## Purpose`
7. `## Trigger`
8. `## Instructions`
9. `## Expected Output`
10. `## Customization Notes`

## Authoring Guidance

- Start from the closest existing template.
- Use the smallest trigger and permission scope that still makes sense.
- Default to read permissions and route writes through `safe-outputs`.
- Prefer `tools.github.toolsets` over older allowlist-style tool declarations.
- If you use schedules, prefer the current `gh-aw` expressions such as `weekly` or `every 1mo` instead of raw cron unless you have a clear need.
- Keep templates broadly reusable: labels, teams, and branch names should be examples, not hidden assumptions.

## High-Value Contributions

The best contributions make the library more concrete, not just larger.

- Deepen an existing template so it produces a clearer, more auditable maintainer action.
- Add a missing high-signal workflow that many repositories actually need.
- Tighten a template that is too generic, too noisy, or too broad in scope.
- Improve README descriptions when template behavior changes enough that the catalog summary drifts.
- Update docs when the public `gh-aw` docs change in a way that affects authoring or rollout.

Prefer one strong workflow over three weak variations of the same idea.

## Validation

The included `.github/workflows/validate.yml` workflow checks that every template includes frontmatter and the required headings. It is a repository-level structure check.

For real workflow validation, run:

```bash
gh aw validate --dir templates/<category>
```

If you change the required structure, update:

- `README.md`
- `docs/format-reference.md`
- `.github/workflows/validate.yml`

## Pull Requests

Use the pull request template and describe the change in plain language. Keep the PR narrowly scoped to one outcome.

Good pull requests for this repository are:

- narrowly scoped to one template or one doc change
- validated against the affected template category before submission
- explicit about whether the change affects user-facing behavior
- easy to audit in one pass

Review is done by the maintainer. Response time varies — if your PR sits for a while, that is expected and does not mean it will be rejected.

## Hard Merge Gates

A pull request must pass all of these before merging:

- affected templates still pass `gh aw validate`
- change stays within repository scope
- no internal or machine-specific files are introduced
- permissions do not expand beyond what the template needs
- public docs are updated if user-facing behavior changed

