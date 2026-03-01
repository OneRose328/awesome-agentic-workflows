# Format Reference

Templates in this repository are community-authored source templates for GitHub Agentic Workflows. They are not official GitHub-authored templates. They are designed to be copied into `.github/workflows/` and compiled with `gh aw compile`.

## Frontmatter

Typical frontmatter looks like this:

```yaml
---
on:
  issues:
    types: [opened, edited]
permissions:
  issues: read
tools:
  github:
    toolsets: [issues, labels]
network: defaults
safe-outputs:
  add-labels:
    max: 3
  add-comment:
    max: 1
---
```

## Body Sections

Each template in this repository uses the same body structure:

1. `# <Title>`
2. `## Purpose`
3. `## Trigger`
4. `## Instructions`
5. `## Expected Output`
6. `## Customization Notes`

## Important Notes

- The Markdown `.md` file is the editable source workflow.
- Official workflow source files belong in `.github/workflows/`.
- Compiled workflows are stored next to them as `.lock.yml` files.
- `tools.github.toolsets` is the current preferred GitHub tool declaration style.
- Current `gh-aw` validation is strict by default, so read permissions plus `safe-outputs` is the safest baseline.
- Schedules should use current `gh-aw` syntax such as `weekly` or fixed intervals like `every 1mo`.

## Validation

This repository's own validation workflow checks only the template library structure. Use `gh aw validate --dir .github/workflows` for real parser validation before `gh aw compile --dir .github/workflows`.

