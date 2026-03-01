# Getting Started

This guide shows how to turn one template from this repository into a real GitHub Agentic Workflow.

The templates in this repository are editable source files, not official GitHub-authored templates and not the final compiled workflow output.

## 1. Pick A Template

Choose the workflow that matches the smallest useful automation you want first. Good starting points:

- `templates/issue-management/auto-triage.md`
- `templates/pr-automation/code-review-assistant.md`
- `templates/release-management/release-checklist.md`

Pick the first workflow by outcome, not by category size:

- If issue intake is noisy, start with one issue workflow
- If reviews are slow, start with one pull-request workflow
- If releases feel inconsistent, start with one release workflow

The first workflow should remove one repeated maintainer task, not redesign your whole repository process in one step.

## 2. Copy The Source File

Copy the source template into your repository:

```bash
mkdir -p .github/workflows
cp templates/issue-management/auto-triage.md .github/workflows/issue-triage.md
```

If you want more than one starting workflow, you do not have to repeat this by hand forever:

- Use `gh aw add OneRose328/awesome-agentic-workflows/templates/...` to import directly from GitHub
- From a local clone, `gh aw add "./templates/<category>/*.md" --non-interactive` can import a whole category at once
- You can pass several workflow specs to one `gh aw add` command, then use a shell loop only if you still want more control

Bulk import is a speed tool, not a rollout strategy. Most repositories should still begin with one or two low-risk workflows and expand only after the first ones behave predictably.

## 3. Customize The Frontmatter

Review and adjust:

- `on`
- `permissions`
- `safe-outputs`
- `tools`
- any repository-specific labels, milestones, reviewers, or branch names

## 4. Compile The Workflow

Install the GitHub CLI extension if needed, validate the workflow directory first, then compile:

```bash
gh extension install github/gh-aw
gh aw validate --dir .github/workflows
gh aw compile --dir .github/workflows
```

This creates `.github/workflows/<name>.lock.yml`.

That `.lock.yml` file is the compiled output. The `.md` file remains the source you keep editing.

## 5. Test In A Low-Risk Way

Start with a workflow that summarizes, comments, or labels through `safe-outputs` before you automate broader behavior. Review the generated output carefully.

## 6. Use A Safe Rollout Order

The lowest-friction path is usually:

1. Start with draft-style workflows that create one reusable artifact, such as release notes, checklists, or summaries.
2. Move to comment-based workflows that help reviewers or maintainers but do not change repository state broadly.
3. Add label-driven routing once your repository labels and triage rules are stable.
4. Expand to security or release coordination workflows only after the earlier steps feel predictable.

## 7. Iterate

The Markdown body can usually be refined faster than frontmatter. Re-check the official docs when changing frontmatter keys or execution behavior.

## 8. Common Mistakes

- Editing the generated `.lock.yml` instead of the Markdown source file
- Copying a template without replacing labels, branch rules, or ownership assumptions
- Starting with a broad operational workflow before proving a low-risk draft or comment workflow
- Treating validation success as proof that the workflow already matches your repository policy
- Forgetting that the real runnable workflow belongs in `.github/workflows/`, not in `templates/`
