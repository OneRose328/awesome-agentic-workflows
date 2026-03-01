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

# Security Scan Notifier

## Purpose
Surface real security scan findings and turn them into clear follow-up actions instead of raw scanner noise.

## Trigger
Run when a pull request is opened, updated, or marked ready for review. The workflow reads security scan results already present in the pull request context — it does not run the scanner itself. If your security scanner posts results as check annotations or comments, this workflow reads those findings and translates them into maintainer-readable guidance.

## Instructions
1. Read the security findings in context: changed files, code paths touched, existing suppressions, and any remediation notes already on the pull request.
2. Separate findings into three buckets: likely real merge blockers, likely real but non-blocking follow-up, and likely scanner noise.
3. Prioritize findings tied to changed code over inherited or unrelated background noise unless the background finding is severe enough to change merge posture.
4. Use safe outputs to leave only the comments needed to make the author and reviewer act: what is risky, where it appears, and whether it likely blocks merge.
5. Summarize the finding in maintainer language. Do not paste raw scanner dumps or long severity tables into the thread.
6. If the signal is uncertain, explicitly recommend human security review instead of pretending the tool can close the question.
7. Keep the scope narrow: actionable follow-up on scan output, not a full manual security audit of the whole pull request.

## Expected Output
- A short, actionable security summary that reduces scanner noise.
- Clear distinction between merge-blocking risk, follow-up work, and likely false positives.

## Customization Notes
- Add your merge-blocking threshold and any severity mapping your team uses.
- If certain scanners are known to be noisy, document the false-positive handling rules here.
- Keep comment volume low so real security findings stay visible.
