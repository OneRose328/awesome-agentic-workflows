# Install and Deploy

This guide covers the standard path from choosing a template to running it in your repository. All `gh aw` commands work on macOS, Linux, and Windows.

## 1. Download This Library

You have two normal ways to get the templates:

### Option A: Clone Or Download The Repository

```bash
git clone https://github.com/OneRose328/awesome-agentic-workflows.git
cd awesome-agentic-workflows
```

If you do not want to use Git, you can also use GitHub's **Code -> Download ZIP** option and extract it locally.

### Option B: Add A Template Directly With `gh aw add`

Import a template straight from GitHub without cloning the full library:

```bash
gh aw add OneRose328/awesome-agentic-workflows/templates/issue-management/auto-triage.md
```

You can also pass more than one workflow spec in one command:

```bash
gh aw add "OneRose328/awesome-agentic-workflows/templates/issue-management/auto-triage.md" "OneRose328/awesome-agentic-workflows/templates/pr-automation/code-review-assistant.md" --non-interactive
```

## 2. Put The Source Workflow In Your Repository

If you used `gh aw add` in step 1, this step is already done — skip to step 3.

If you cloned the library, copy the template into the repository where you want the workflow to run:

```bash
# macOS / Linux / Windows (Git Bash or WSL)
mkdir -p .github/workflows
cp awesome-agentic-workflows/templates/issue-management/auto-triage.md .github/workflows/issue-triage.md
```

## 3. Customize The Workflow

Edit the copied `.md` source file in your own repository and adjust:

- `on`
- `permissions`
- `safe-outputs`
- `tools`
- labels, reviewers, branch names, or repository-specific instructions

For the safest first rollout:

- keep permissions read-only unless you have a clear reason not to
- express write actions through `safe-outputs`
- start with a workflow that comments, summarizes, drafts, or labels

## 4. Validate And Compile

Install the GitHub CLI extension if needed, then validate before compiling:

```bash
gh extension install github/gh-aw
gh aw validate --dir .github/workflows
gh aw compile --dir .github/workflows
```

This creates:

- `.github/workflows/<name>.md` as your editable source file
- `.github/workflows/<name>.lock.yml` as the compiled workflow GitHub Actions will run

Do not treat the `.lock.yml` file as your primary authoring file.

## 5. Commit And Push

Commit both files:

```bash
git add .github/workflows/<name>.md .github/workflows/<name>.lock.yml
git commit -m "feat: add <name> agentic workflow"
git push
```

## 6. Enable And Test In GitHub

After pushing:

1. Open your repository on GitHub.
2. Make sure GitHub Actions is enabled for the repository.
3. Trigger the workflow using a safe, low-risk event first.
4. Check the **Actions** tab to confirm the run starts and completes as expected.

Good first tests:

- open a test issue
- update a test pull request
- run on a manual or low-impact schedule

Avoid starting with broad write behavior until you trust the workflow output.
