# Awesome GitHub Agentic Workflows

[English](README.md) | 简体中文

[![GitHub Stars](https://img.shields.io/github/stars/OneRose328/awesome-agentic-workflows?style=for-the-badge&color=f59e0b)](https://github.com/OneRose328/awesome-agentic-workflows/stargazers)
[![模板数量](https://img.shields.io/badge/模板数量-56-0a7ea4?style=for-the-badge)](#模板库)
[![GitHub Agentic Workflows](https://img.shields.io/badge/GitHub-Agentic%20Workflows-24292f?style=for-the-badge&logo=github)](https://github.github.com/gh-aw/)
[![License: MIT](https://img.shields.io/badge/License-MIT-2563eb.svg?style=for-the-badge)](LICENSE)
[![欢迎贡献](https://img.shields.io/badge/欢迎贡献-16a34a.svg?style=for-the-badge)](CONTRIBUTING.md)

**不要再从零开始写 GitHub 工作流自动化了。**

56 个即用型 [GitHub Agentic Workflow](https://github.github.com/gh-aw/) 模板——复制一个，改三行，你的仓库就能自动处理 Issue 分类、PR 审查、发布说明和密钥检测。每个模板专注单一的维护场景，已通过当前 `gh-aw` CLI 验证，一分钟内可完成审查。

> **前置要求：** [GitHub Agentic Workflows](https://github.github.com/gh-aw/)（目前处于技术预览阶段）。这不是标准的 GitHub Actions YAML 工作流——需要用 `gh aw` CLI 将 Markdown 编译成可运行的工作流。

---

## 包含内容

| | |
|---|---|
| **56 个模板** | 分 7 大类：Issue 管理、PR 自动化、发布管理、代码质量、社区运营、安全、开发者体验 |
| **更安全的默认值** | 所有模板使用只读权限 + `safe-outputs`——写操作明确且有边界限制 |
| **一个模板一个目标** | 没有多功能助手。每个工作流只做一件可验证的事。 |
| **复制即用** | 纯 Markdown，无框架依赖。只需修改仓库专属的几行配置。 |

## 快速开始

支持 macOS、Linux 和 Windows。

```bash
# 1. 从下方模板库选择一个，复制到你的仓库
cp templates/issue-management/auto-triage.md 你的仓库/.github/workflows/auto-triage.md

# 2. 修改仓库专属配置（标签规则、owner 规则、说明文字）
# 3. 验证并编译
gh aw validate --dir .github/workflows
gh aw compile  --dir .github/workflows

# 4. 同时提交 .md 源文件和生成的 .lock.yml
```

或直接从 GitHub 添加：

```bash
gh aw add OneRose328/awesome-agentic-workflows/templates/issue-management/auto-triage.md
```

## 从哪里开始

根据你的情况选对应的行，这是风险最低、收益最高的入手点：

| 你的情况 | 第一个模板 | 第二个模板 |
| --- | --- | --- |
| Issue 堆积无人处理 | [Auto Triage](templates/issue-management/auto-triage.md) | [First Response](templates/issue-management/first-response.md) |
| PR 长期无人审查 | [Code Review Assistant](templates/pr-automation/code-review-assistant.md) | [Auto Assign Reviewer](templates/pr-automation/auto-assign-reviewer.md) |
| 每次发版都要手写发布说明 | [Release Notes Generator](templates/release-management/release-notes-generator.md) | [Release Checklist](templates/release-management/release-checklist.md) |
| 担心提交中有密钥泄露 | [Secret Leak Detector](templates/security/secret-leak-detector.md) | [Security Scan Notifier](templates/pr-automation/security-scan-notifier.md) |
| 新贡献者总是找不到方向 | [Onboarding Guide](templates/developer-experience/onboarding-guide.md) | [Setup Validator](templates/developer-experience/setup-validator.md) |

**部署建议：** 先从只评论或只生成草稿的工作流开始。确认它在你仓库里噪音低，再启用自动打标签或自动路由的模板。

## 源文件 vs 编译产物

```
templates/issue-management/auto-triage.md   ← 本仓库（你复制和编辑的）
.github/workflows/auto-triage.md            ← 你的仓库（定制后的源文件）
.github/workflows/auto-triage.lock.yml      ← 你的仓库（编译产物，不要手动编辑）
```

编辑 `.md` 源文件，运行 `gh aw compile`，提交两个文件。不要手动编辑 `.lock.yml`。

## 常见问题

**需要 GitHub Copilot 才能用这些模板吗？**

不需要。你需要 GitHub Agentic Workflows 工具链，但不是 Copilot 专属功能。这些模板关注的是工作流结构和任务设计。

**模板可以直接照搬上线吗？**

通常不建议。模板是强力的起点，但你还是应该替换标签、路径、owner 规则和仓库专属说明，再当作生产环境使用。

**需要手动编辑 `.lock.yml` 吗？**

不需要。把 `.md` 文件当你的编辑对象。`.lock.yml` 是编译产物，由 `gh aw compile` 生成。

**这些模板在生产环境安全吗？**

模板采用了更安全的默认值，但你仍应先从低风险工作流开始，验证、编译，在受控环境下测试后再全面使用。

**需要把 56 个全部用上吗？**

不需要。大多数仓库从 1-2 个低风险工作流开始就够了，等第一个稳定可靠后再扩展。

---

## 模板库

### 分类概览

| 分类 | 数量 | 目录 |
| --- | ---: | --- |
| Issue 管理 | 10 | templates/issue-management/ |
| PR 自动化 | 10 | templates/pr-automation/ |
| 发布管理 | 8 | templates/release-management/ |
| 代码质量 | 8 | templates/code-quality/ |
| 社区运营 | 8 | templates/community/ |
| 安全 | 6 | templates/security/ |
| 开发者体验 | 6 | templates/developer-experience/ |

### Issue 管理

| 模板 | 文件 | 说明 |
| --- | --- | --- |
| [Auto Label](templates/issue-management/auto-label.md) | auto-label.md | 为新建或更新的 Issue 自动打上初始标签集。 |
| [Auto Triage](templates/issue-management/auto-triage.md) | auto-triage.md | 按优先级、范围和负责人对 Issue 分类。 |
| [Duplicate Detector](templates/issue-management/duplicate-detector.md) | duplicate-detector.md | 标记疑似重复的 Issue，并链接到对应的已有讨论。 |
| [Stale Issue Closer](templates/issue-management/stale-issue-closer.md) | stale-issue-closer.md | 找出长期不活跃的 Issue，推进结构化的过期处理流程。 |
| [Bug Report Validator](templates/issue-management/bug-report-validator.md) | bug-report-validator.md | 区分可操作的 Bug 报告与信息不完整的提交，只询问最关键的缺失信息。 |
| [Feature Request Analyzer](templates/issue-management/feature-request-analyzer.md) | feature-request-analyzer.md | 基于价值、范围和缺失上下文，将功能需求归入明确的下一步状态。 |
| [First Response](templates/issue-management/first-response.md) | first-response.md | 发送有针对性的首次回复，明确下一步行动，不做空洞承诺。 |
| [Milestone Assigner](templates/issue-management/milestone-assigner.md) | milestone-assigner.md | 根据 Issue 范围、紧急程度和发布计划，分配最合适的里程碑。 |
| [Issue Summarizer](templates/issue-management/issue-summarizer.md) | issue-summarizer.md | 生成 Issue 活动摘要和未解决阻塞点的简报。 |
| [Escalation Detector](templates/issue-management/escalation-detector.md) | escalation-detector.md | 根据严重性信号，从普通 Issue 中识别出真正需要升级处理的问题。 |

### PR 自动化

| 模板 | 文件 | 说明 |
| --- | --- | --- |
| [Code Review Assistant](templates/pr-automation/code-review-assistant.md) | code-review-assistant.md | 执行第一轮审查，标出正确性问题和风险热点。 |
| [PR Size Checker](templates/pr-automation/pr-size-checker.md) | pr-size-checker.md | 当 PR 大到可能影响审查或合并质量时发出警告。 |
| [Changelog Generator](templates/pr-automation/changelog-generator.md) | changelog-generator.md | 从 PR 自动生成发布说明草稿。 |
| [Merge Conflict Helper](templates/pr-automation/merge-conflict-helper.md) | merge-conflict-helper.md | 标出可能存在合并冲突的文件和区域。 |
| [Test Coverage Reminder](templates/pr-automation/test-coverage-reminder.md) | test-coverage-reminder.md | 标记看起来测试不足的行为变更，并提示缺失的测试场景。 |
| [Documentation Checker](templates/pr-automation/documentation-checker.md) | documentation-checker.md | 检测面向用户的改动是否造成文档不同步，忽略纯内部重构。 |
| [PR Summary Generator](templates/pr-automation/pr-summary-generator.md) | pr-summary-generator.md | 在审查开始前为审查者生成结构化摘要。 |
| [Security Scan Notifier](templates/pr-automation/security-scan-notifier.md) | security-scan-notifier.md | 将安全扫描结果转化为明确的阻塞项、待跟进项或疑似误报的可操作指导。 |
| [Auto Assign Reviewer](templates/pr-automation/auto-assign-reviewer.md) | auto-assign-reviewer.md | 推荐最合适的主审查人，并说明理由。 |
| [Breaking Change Detector](templates/pr-automation/breaking-change-detector.md) | breaking-change-detector.md | 标记可能破坏下游用户的接口或行为变更。 |

### 发布管理

| 模板 | 文件 | 说明 |
| --- | --- | --- |
| [Release Notes Generator](templates/release-management/release-notes-generator.md) | release-notes-generator.md | 从最近合并的 PR 生成打磨好的发布说明。 |
| [Version Bumper](templates/release-management/version-bumper.md) | version-bumper.md | 根据可见的发布影响和兼容性，推荐下一个版本号。 |
| [Release Announcement](templates/release-management/release-announcement.md) | release-announcement.md | 撰写简洁的发布公告草稿，以用户可见的价值为主体。 |
| [Dependency Update Summary](templates/release-management/dependency-update-summary.md) | dependency-update-summary.md | 只汇总对发布置信度有实质影响的依赖升级。 |
| [Migration Guide Generator](templates/release-management/migration-guide-generator.md) | migration-guide-generator.md | 当发布引入破坏性变更或高风险升级步骤时，生成迁移指南。 |
| [Release Checklist](templates/release-management/release-checklist.md) | release-checklist.md | 生成包含就绪项、阻塞项和待确认项的发布检查清单。 |
| [Hotfix Coordinator](templates/release-management/hotfix-coordinator.md) | hotfix-coordinator.md | 让紧急修复保持在最小安全路径上推进，避免引入额外风险。 |
| [Beta Feedback Collector](templates/release-management/beta-feedback-collector.md) | beta-feedback-collector.md | 将 Beta 反馈聚类为阻塞项、主题和待跟进行动，服务于发布就绪判断。 |

### 代码质量

| 模板 | 文件 | 说明 |
| --- | --- | --- |
| [Architecture Reviewer](templates/code-quality/architecture-reviewer.md) | architecture-reviewer.md | 检查变更是否符合现有架构和边界约束。 |
| [Performance Analyzer](templates/code-quality/performance-analyzer.md) | performance-analyzer.md | 标记可能的性能回归或新增的高开销代码路径。 |
| [Tech Debt Identifier](templates/code-quality/tech-debt-identifier.md) | tech-debt-identifier.md | 识别当前变更引入或暴露的具体技术债。 |
| [API Consistency Checker](templates/code-quality/api-consistency-checker.md) | api-consistency-checker.md | 检查面向 API 的变更是否存在契约漂移、Schema 不匹配或兼容性问题。 |
| [Error Handling Reviewer](templates/code-quality/error-handling-reviewer.md) | error-handling-reviewer.md | 检查新的失败路径是否处理清晰，不会掩盖线上问题。 |
| [Accessibility Checker](templates/code-quality/accessibility-checker.md) | accessibility-checker.md | 检查面向用户界面的变更是否存在键盘操作、屏幕阅读器或语义回归。 |
| [Naming Convention Enforcer](templates/code-quality/naming-convention-enforcer.md) | naming-convention-enforcer.md | 标记会影响可读性或可搜索性的持久性命名漂移。 |
| [Complexity Analyzer](templates/code-quality/complexity-analyzer.md) | complexity-analyzer.md | 标出逻辑明显变得更难理解或更难安全审查的代码。 |

### 社区运营

| 模板 | 文件 | 说明 |
| --- | --- | --- |
| [New Contributor Welcome](templates/community/new-contributor-welcome.md) | new-contributor-welcome.md | 用最少的引导语欢迎首次贡献者，帮助他们快速定向。 |
| [Good First Issue Tagger](templates/community/good-first-issue-tagger.md) | good-first-issue-tagger.md | 识别对新贡献者真正安全且可完成的 Issue。 |
| [Community Health Report](templates/community/community-health-report.md) | community-health-report.md | 在积压问题积累前，汇总响应健康度、贡献流量和支持负载。 |
| [Discussion Moderator](templates/community/discussion-moderator.md) | discussion-moderator.md | 仅在讨论真正需要干预时，执行低噪音的管理或路由操作。 |
| [Contributor Recognition](templates/community/contributor-recognition.md) | contributor-recognition.md | 以具体、公正且可发布的方式突出贡献者的成果。 |
| [FAQ Responder](templates/community/faq-responder.md) | faq-responder.md | 对真正的高频问题发布简短、可复用的回复，不对边缘情况随意猜测。 |
| [Hacktoberfest Manager](templates/community/hacktoberfest-manager.md) | hacktoberfest-manager.md | 为 Hacktoberfest 等季节性活动筛选适合贡献的 Issue。 |
| [Roadmap Updater](templates/community/roadmap-updater.md) | roadmap-updater.md | 汇总应影响路线图沟通的 Issue 和讨论信号。 |

### 安全

| 模板 | 文件 | 说明 |
| --- | --- | --- |
| [Vulnerability Reporter](templates/security/vulnerability-reporter.md) | vulnerability-reporter.md | 通过更安全的接收和跟进流程处理漏洞报告。 |
| [Secret Leak Detector](templates/security/secret-leak-detector.md) | secret-leak-detector.md | 标记 diff 或仓库内容中可能存在的凭据泄露。 |
| [Dependency Vulnerability Alert](templates/security/dependency-vulnerability-alert.md) | dependency-vulnerability-alert.md | 汇总存在漏洞的依赖及最安全的近期修复路径。 |
| [Security Policy Enforcer](templates/security/security-policy-enforcer.md) | security-policy-enforcer.md | 根据披露规则、审查要求和保护策略检查敏感变更。 |
| [CVE Tracker](templates/security/cve-tracker.md) | cve-tracker.md | 追踪活跃 CVE，清晰区分暴露面、缓解措施和不确定项。 |
| [Security Review Requester](templates/security/security-review-requester.md) | security-review-requester.md | 只在变更确实带来实质安全风险时，才请求专项安全审查。 |

### 开发者体验

| 模板 | 文件 | 说明 |
| --- | --- | --- |
| [Onboarding Guide](templates/developer-experience/onboarding-guide.md) | onboarding-guide.md | 生成从首次克隆到第一次安全提交的分步入职清单。 |
| [Setup Validator](templates/developer-experience/setup-validator.md) | setup-validator.md | 检查新贡献者是否仍能在无隐藏障碍的情况下完成本地环境搭建。 |
| [Dev Diary](templates/developer-experience/dev-diary.md) | dev-diary.md | 生成简洁的开发日志，让维护者能快速还原近期进展。 |
| [Sprint Planner](templates/developer-experience/sprint-planner.md) | sprint-planner.md | 结合 Backlog、依赖和维护压力，生成可落地的 Sprint 范围草稿。 |
| [Standup Generator](templates/developer-experience/standup-generator.md) | standup-generator.md | 根据近期进展和阻塞项，生成简短的站会更新摘要。 |
| [Retrospective Helper](templates/developer-experience/retrospective-helper.md) | retrospective-helper.md | 准备包含可操作亮点、痛点和后续行动的回顾会议草稿。 |

---

## 准确性说明

本仓库与 2026 年 3 月 1 日公开的 GitHub Agentic Workflows 文档对齐。由于该功能仍处于早期开发阶段，在生产环境启用工作流前，请先核对官方文档。

官方参考文档：

- [CLI 命令](https://github.github.com/gh-aw/setup/cli/)
- [创建 Agentic Workflows](https://github.github.com/gh-aw/setup/creating-workflows/)
- [工作流结构](https://github.github.com/gh-aw/reference/workflow-structure/)

## 贡献

贡献规则和模板结构要求见 [CONTRIBUTING.md](CONTRIBUTING.md)。

CI 会在 push 和 PR 时自动检查模板结构。Pull Request 模板会要求你说明改了什么、验证了什么。

## License

基于 [MIT License](LICENSE) 发布。
