# 安装与部署

这份文档说明如何把模板放进你自己的仓库并完成部署。所有 `gh aw` 命令在 macOS、Linux 和 Windows 上均可使用。

## 1. 先拿到模板库

你有两种常用方式：

### 方式 A：克隆或下载整个仓库

```bash
git clone https://github.com/OneRose328/awesome-agentic-workflows.git
cd awesome-agentic-workflows
```

如果你不想用 Git，也可以在 GitHub 页面使用 **Code -> Download ZIP** 下载并解压。

### 方式 B：直接用 `gh aw add` 导入模板

不克隆整个仓库，直接从 GitHub 导入单个模板：

```bash
gh aw add OneRose328/awesome-agentic-workflows/templates/issue-management/auto-triage.md
```

如果你想一次导入多个模板，也可以一条命令传多个参数：

```bash
gh aw add "OneRose328/awesome-agentic-workflows/templates/issue-management/auto-triage.md" "OneRose328/awesome-agentic-workflows/templates/pr-automation/code-review-assistant.md" --non-interactive
```

## 2. 把源工作流放进你自己的仓库

如果你在第一步用的是 `gh aw add`，这一步已经自动完成——直接跳到第 3 步。

如果你克隆了整个仓库，在你真正想运行工作流的仓库里执行：

```bash
# macOS / Linux / Windows（Git Bash 或 WSL）
mkdir -p .github/workflows
cp awesome-agentic-workflows/templates/issue-management/auto-triage.md .github/workflows/issue-triage.md
```

## 3. 修改工作流

编辑你自己仓库里的 `.md` 源文件，重点看这些地方：

- `on`
- `permissions`
- `safe-outputs`
- `tools`
- 标签、reviewer、分支名、仓库专属说明

第一轮建议遵守这几个原则：

- 权限优先只读
- 写操作优先通过 `safe-outputs`
- 先用会评论、会总结、会草拟内容的低风险流程

## 4. 验证并编译

如果还没装扩展，先装：

```bash
gh extension install github/gh-aw
```

然后先验证，再编译：

```bash
gh aw validate --dir .github/workflows
gh aw compile --dir .github/workflows
```

完成后你会得到：

- `.github/workflows/<name>.md`：你持续编辑的源文件
- `.github/workflows/<name>.lock.yml`：GitHub Actions 实际运行的编译产物

不要把 `.lock.yml` 当成主要编辑文件。

## 5. 提交并推送

```bash
git add .github/workflows/<name>.md .github/workflows/<name>.lock.yml
git commit -m "feat: add <name> agentic workflow"
git push
```

## 6. 到 GitHub 上测试

推送后：

1. 打开你的 GitHub 仓库页面
2. 确认 GitHub Actions 已启用
3. 用一个低风险事件先触发一次
4. 到 **Actions** 页面检查这次运行是否正常

适合第一轮测试的方式：

- 新建一个测试 issue
- 更新一个测试 PR
- 使用低影响的手动或定时触发

不要一开始就启用高风险、大范围写入行为。
