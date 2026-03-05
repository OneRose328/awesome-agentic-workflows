# Awesome GitHub Agentic Workflows

English | [Chinese (Simplified)](README.zh-CN.md)

[![GitHub Stars](https://img.shields.io/github/stars/OneRose328/awesome-agentic-workflows?style=for-the-badge&color=f59e0b)](https://github.com/OneRose328/awesome-agentic-workflows/stargazers)
[![Templates](https://img.shields.io/badge/templates-56-0a7ea4?style=for-the-badge)](#template-library)
[![GitHub Agentic Workflows](https://img.shields.io/badge/GitHub-Agentic%20Workflows-24292f?style=for-the-badge&logo=github)](https://github.github.com/gh-aw/)
[![License: MIT](https://img.shields.io/badge/License-MIT-2563eb.svg?style=for-the-badge)](LICENSE)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-16a34a.svg?style=for-the-badge)](CONTRIBUTING.md)

**Stop writing GitHub workflow automation from scratch.**

56 ready-to-use [GitHub Agentic Workflow](https://github.github.com/gh-aw/) templates — copy one, adapt three lines, and your repository handles issue triage, PR review, release notes, and secret detection automatically. Each template is written around one narrow maintainer outcome, tested against the current `gh-aw` CLI, and designed to be audited in under a minute.

> **Requires:** [GitHub Agentic Workflows](https://github.github.com/gh-aw/) (currently in technical preview). These are not standard GitHub Actions YAML workflows — they use the `gh aw` CLI to compile Markdown into runnable workflows.

---

## What's Inside

| | |
|---|---|
| **56 templates** | Across 7 categories: issue management, PR automation, release, code quality, community, security, developer experience |
| **Safer defaults** | All templates use read permissions + `safe-outputs` — write actions are explicit and bounded |
| **One outcome per template** | No multi-purpose assistants. Each workflow does one thing you can verify. |
| **Copy-paste ready** | Plain Markdown. No framework. Adapt the three lines that are specific to your repo. |

## Quick Start

Works on macOS, Linux, and Windows.

```bash
# 1. Pick a template from the library below and copy it to your repo
cp templates/issue-management/auto-triage.md /your-repo/.github/workflows/auto-triage.md

# 2. Edit the three repository-specific lines (labels, ownership rules, instructions)
# 3. Validate and compile
gh aw validate --dir .github/workflows
gh aw compile  --dir .github/workflows

# 4. Commit both the .md source and the generated .lock.yml
```

Or add directly from GitHub:

```bash
gh aw add OneRose328/awesome-agentic-workflows/templates/issue-management/auto-triage.md
```

## Where to Start

Pick the row that matches your situation. These are the highest-leverage, lowest-risk entry points:

| Your Situation | First Template | Second Template |
| --- | --- | --- |
| Issues piling up with no triage | [Auto Triage](templates/issue-management/auto-triage.md) | [First Response](templates/issue-management/first-response.md) |
| PRs sitting unreviewed | [Code Review Assistant](templates/pr-automation/code-review-assistant.md) | [Auto Assign Reviewer](templates/pr-automation/auto-assign-reviewer.md) |
| Release notes written manually every time | [Release Notes Generator](templates/release-management/release-notes-generator.md) | [Release Checklist](templates/release-management/release-checklist.md) |
| Worried about secrets in commits | [Secret Leak Detector](templates/security/secret-leak-detector.md) | [Security Scan Notifier](templates/pr-automation/security-scan-notifier.md) |
| New contributors keep getting lost | [Onboarding Guide](templates/developer-experience/onboarding-guide.md) | [Setup Validator](templates/developer-experience/setup-validator.md) |

**Rollout advice:** Start with one workflow that only comments or drafts. Prove it's low-noise in your repository before enabling anything that labels or routes automatically.

## Source File vs Compiled File

```
templates/issue-management/auto-triage.md   ← this repo (what you copy and edit)
.github/workflows/auto-triage.md            ← your repo (your customized source)
.github/workflows/auto-triage.lock.yml      ← your repo (compiled, do not hand-edit)
```

Edit the `.md` source. Run `gh aw compile`. Commit both files. Never hand-edit `.lock.yml`.

## FAQ

**Do I need GitHub Copilot to use these templates?**

No. You need the GitHub Agentic Workflows toolchain, but the workflow engine can still vary by setup. These templates are about workflow structure and task design, not a Copilot-only feature pack.

**Can I use the templates exactly as they are?**

Usually not. They are strong starting points, but you should still replace labels, paths, ownership rules, and repository-specific instructions before treating them as production-ready.

**Do I edit the `.lock.yml` file?**

No. Treat the Markdown `.md` file as the source you edit. The `.lock.yml` file is the compiled output generated from that source.

**Are these templates safe to run in production immediately?**

They are written around safer defaults, but you should still start with low-risk workflows, validate them, compile them, and test them in a controlled repository context before broad use.

**Do I need all 56 templates?**

No. Most repositories should start with one or two low-risk workflows and only expand once the first ones are predictable and useful.

**Why keep templates in `templates/` if real workflows live in `.github/workflows/`?**

Because this repository is a library. `templates/` is the catalog of reusable source templates. In your own repository, the workflows you actually run belong in `.github/workflows/`.

## Template Library

### Category Overview

| Category | Count | Directory |
| --- | ---: | --- |
| Issue Management | 10 | templates/issue-management/ |
| PR Automation | 10 | templates/pr-automation/ |
| Release Management | 8 | templates/release-management/ |
| Code Quality | 8 | templates/code-quality/ |
| Community | 8 | templates/community/ |
| Security | 6 | templates/security/ |
| Developer Experience | 6 | templates/developer-experience/ |

### Issue Management

| Template | File | Description |
| --- | --- | --- |
| [Auto Label](templates/issue-management/auto-label.md) | auto-label.md | Automatically applies an initial label set to a newly opened or updated issue. |
| [Auto Triage](templates/issue-management/auto-triage.md) | auto-triage.md | Classifies an issue by priority, scope, and next owner. |
| [Duplicate Detector](templates/issue-management/duplicate-detector.md) | duplicate-detector.md | Flags likely duplicate issues and links maintainers to the matching thread. |
| [Stale Issue Closer](templates/issue-management/stale-issue-closer.md) | stale-issue-closer.md | Finds inactive issues and proposes a structured stale workflow. |
| [Bug Report Validator](templates/issue-management/bug-report-validator.md) | bug-report-validator.md | Separates actionable bug reports from incomplete intake and asks for the one missing detail that matters most. |
| [Feature Request Analyzer](templates/issue-management/feature-request-analyzer.md) | feature-request-analyzer.md | Triages a feature request into a clear next state based on value, scope, and missing context. |
| [First Response](templates/issue-management/first-response.md) | first-response.md | Posts a specific first-touch reply that sets the next step without making promises. |
| [Milestone Assigner](templates/issue-management/milestone-assigner.md) | milestone-assigner.md | Assigns the most appropriate milestone based on issue scope, urgency, and release fit. |
| [Issue Summarizer](templates/issue-management/issue-summarizer.md) | issue-summarizer.md | Builds a concise digest of issue activity and open blockers. |
| [Escalation Detector](templates/issue-management/escalation-detector.md) | escalation-detector.md | Separates true escalation candidates from normal issue intake based on severity signals. |

### PR Automation

| Template | File | Description |
| --- | --- | --- |
| [Code Review Assistant](templates/pr-automation/code-review-assistant.md) | code-review-assistant.md | Performs a first-pass review and surfaces correctness or risk hotspots. |
| [PR Size Checker](templates/pr-automation/pr-size-checker.md) | pr-size-checker.md | Warns when a pull request is large enough to create review or merge risk. |
| [Changelog Generator](templates/pr-automation/changelog-generator.md) | changelog-generator.md | Drafts a release-note-ready changelog entry from the pull request. |
| [Merge Conflict Helper](templates/pr-automation/merge-conflict-helper.md) | merge-conflict-helper.md | Highlights likely merge conflicts and the files most likely to need attention. |
| [Test Coverage Reminder](templates/pr-automation/test-coverage-reminder.md) | test-coverage-reminder.md | Flags behavior changes that appear under-tested and suggests the missing scenario. |
| [Documentation Checker](templates/pr-automation/documentation-checker.md) | documentation-checker.md | Flags reader-facing changes that create real docs drift without spamming internal-only refactors. |
| [PR Summary Generator](templates/pr-automation/pr-summary-generator.md) | pr-summary-generator.md | Creates a structured summary for reviewers before full review starts. |
| [Security Scan Notifier](templates/pr-automation/security-scan-notifier.md) | security-scan-notifier.md | Turns scanner output into clear blocker, follow-up, or likely-noise guidance for reviewers. |
| [Auto Assign Reviewer](templates/pr-automation/auto-assign-reviewer.md) | auto-assign-reviewer.md | Recommends the primary reviewer lane and explains why that lane should own first review. |
| [Breaking Change Detector](templates/pr-automation/breaking-change-detector.md) | breaking-change-detector.md | Flags contract or behavior changes that may break downstream users. |

### Release Management

| Template | File | Description |
| --- | --- | --- |
| [Release Notes Generator](templates/release-management/release-notes-generator.md) | release-notes-generator.md | Builds polished release notes from the latest merge window. |
| [Version Bumper](templates/release-management/version-bumper.md) | version-bumper.md | Recommends the next version bump based on visible release impact and compatibility. |
| [Release Announcement](templates/release-management/release-announcement.md) | release-announcement.md | Drafts a concise launch announcement that leads with user-visible value and only necessary upgrade cautions. |
| [Dependency Update Summary](templates/release-management/dependency-update-summary.md) | dependency-update-summary.md | Summarizes only the dependency upgrades that materially affect release confidence. |
| [Migration Guide Generator](templates/release-management/migration-guide-generator.md) | migration-guide-generator.md | Creates an upgrade guide when a release introduces breaking changes or risky upgrade steps. |
| [Release Checklist](templates/release-management/release-checklist.md) | release-checklist.md | Builds a real release-owner checklist with ready items, blockers, and unknowns. |
| [Hotfix Coordinator](templates/release-management/hotfix-coordinator.md) | hotfix-coordinator.md | Keeps an urgent hotfix aligned on the smallest safe path to production recovery. |
| [Beta Feedback Collector](templates/release-management/beta-feedback-collector.md) | beta-feedback-collector.md | Clusters beta feedback into blockers, themes, and follow-up actions for release readiness. |

### Code Quality

| Template | File | Description |
| --- | --- | --- |
| [Architecture Reviewer](templates/code-quality/architecture-reviewer.md) | architecture-reviewer.md | Checks whether a change fits existing architecture and boundaries. |
| [Performance Analyzer](templates/code-quality/performance-analyzer.md) | performance-analyzer.md | Flags likely performance regressions or expensive new code paths. |
| [Tech Debt Identifier](templates/code-quality/tech-debt-identifier.md) | tech-debt-identifier.md | Identifies concrete maintenance debt introduced or exposed by the current change. |
| [API Consistency Checker](templates/code-quality/api-consistency-checker.md) | api-consistency-checker.md | Reviews API-facing changes for contract drift, schema mismatch, and compatibility issues. |
| [Error Handling Reviewer](templates/code-quality/error-handling-reviewer.md) | error-handling-reviewer.md | Checks whether new failure paths are handled clearly and without hiding incidents. |
| [Accessibility Checker](templates/code-quality/accessibility-checker.md) | accessibility-checker.md | Reviews UI-facing changes for concrete keyboard, screen-reader, and semantics regressions. |
| [Naming Convention Enforcer](templates/code-quality/naming-convention-enforcer.md) | naming-convention-enforcer.md | Flags durable naming drift that would hurt readability or searchability. |
| [Complexity Analyzer](templates/code-quality/complexity-analyzer.md) | complexity-analyzer.md | Highlights logic that has become materially harder to reason about or review safely. |

### Community

| Template | File | Description |
| --- | --- | --- |
| [New Contributor Welcome](templates/community/new-contributor-welcome.md) | new-contributor-welcome.md | Welcomes first-time contributors with the minimum guidance needed to get oriented. |
| [Good First Issue Tagger](templates/community/good-first-issue-tagger.md) | good-first-issue-tagger.md | Identifies issues that are genuinely safe and realistic for new contributors. |
| [Community Health Report](templates/community/community-health-report.md) | community-health-report.md | Summarizes response health, contribution flow, and support load before backlog drag builds. |
| [Discussion Moderator](templates/community/discussion-moderator.md) | discussion-moderator.md | Applies low-noise moderation or routing only when a discussion actually needs intervention. |
| [Contributor Recognition](templates/community/contributor-recognition.md) | contributor-recognition.md | Highlights contributor wins in a way that feels specific, fair, and publishable. |
| [FAQ Responder](templates/community/faq-responder.md) | faq-responder.md | Posts short, reusable answers for true FAQs without guessing on edge cases. |
| [Hacktoberfest Manager](templates/community/hacktoberfest-manager.md) | hacktoberfest-manager.md | Curates contribution-ready issues for seasonal contributor events. |
| [Roadmap Updater](templates/community/roadmap-updater.md) | roadmap-updater.md | Summarizes issue and discussion signals that should influence roadmap communication. |

### Security

| Template | File | Description |
| --- | --- | --- |
| [Vulnerability Reporter](templates/security/vulnerability-reporter.md) | vulnerability-reporter.md | Routes vulnerability reports through a safer intake and follow-up flow. |
| [Secret Leak Detector](templates/security/secret-leak-detector.md) | secret-leak-detector.md | Flags possible credential leaks in diffs or repository content. |
| [Dependency Vulnerability Alert](templates/security/dependency-vulnerability-alert.md) | dependency-vulnerability-alert.md | Summarizes vulnerable dependencies and the safest near-term remediation path. |
| [Security Policy Enforcer](templates/security/security-policy-enforcer.md) | security-policy-enforcer.md | Checks policy-sensitive changes against disclosure, review, and protection rules. |
| [CVE Tracker](templates/security/cve-tracker.md) | cve-tracker.md | Tracks active CVEs with clear separation between exposure, mitigation, and uncertainty. |
| [Security Review Requester](templates/security/security-review-requester.md) | security-review-requester.md | Requests specialized security review only when a change materially shifts security risk. |

### Developer Experience

| Template | File | Description |
| --- | --- | --- |
| [Onboarding Guide](templates/developer-experience/onboarding-guide.md) | onboarding-guide.md | Creates a step-by-step onboarding checklist from fresh clone to first safe contribution. |
| [Setup Validator](templates/developer-experience/setup-validator.md) | setup-validator.md | Checks whether a fresh contributor can still reach a working local setup without hidden blockers. |
| [Dev Diary](templates/developer-experience/dev-diary.md) | dev-diary.md | Produces concise development notes so maintainers can reconstruct recent progress quickly. |
| [Sprint Planner](templates/developer-experience/sprint-planner.md) | sprint-planner.md | Builds a realistic draft sprint scope from backlog, dependencies, and maintenance pressure. |
| [Standup Generator](templates/developer-experience/standup-generator.md) | standup-generator.md | Creates a short standup summary from recent progress and blockers. |
| [Retrospective Helper](templates/developer-experience/retrospective-helper.md) | retrospective-helper.md | Prepares a retrospective draft with actionable wins, pain points, and follow-up actions. |

## Accuracy Notes

This repository is aligned with the public GitHub Agentic Workflows documentation available on March 1, 2026. Because the feature is still in early development, re-check the official docs before enabling a workflow in production.

For current behavior, re-check these official references before making compatibility-sensitive changes:

- [CLI Commands](https://github.github.com/gh-aw/setup/cli/)
- [Creating Agentic Workflows](https://github.github.com/gh-aw/setup/creating-workflows/)
- [Workflow Structure](https://github.github.com/gh-aw/reference/workflow-structure/)

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for the authoring checklist, structure rules, and validation expectations.

This repository is set up to keep contribution review lightweight:

- `.github/pull_request_template.md` asks contributors to explain what changed and what they validated
- `.github/workflows/validate.yml` checks template structure on pushes and pull requests

The intent is simple: use CI and clear pull request scope as the hard merge gates, and keep review expectations easy to understand.

## License

Released under the [MIT License](LICENSE).