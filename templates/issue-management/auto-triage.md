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

# Auto Triage

## Purpose
Classifies an issue by priority, scope, and next owner.

## Trigger
Run when a new issue is opened or when an edited issue materially changes scope, reproduction details, or urgency.

## Instructions
1. Read the issue title, body, template fields, linked stack traces, screenshots, and any labels already present.
2. Classify the issue into the smallest accurate queue: bug, feature request, docs, support, performance, security, or maintenance.
3. Infer urgency from concrete signals only: production outage, data loss, security exposure, wide user impact, broken release path, or blocker for a time-sensitive milestone.
4. Apply no more than three labels that capture type, priority, and affected area. Do not invent labels that are not clearly implied by the repository taxonomy.
5. If the report is missing required details, leave one concise follow-up comment listing only the missing items that block triage.
6. If the issue looks security-sensitive or incident-like, avoid public speculation and route it into the highest-priority path with a short explanation.
7. Stop when confidence is low. A precise partial triage is better than an overconfident full classification.

## Expected Output
- A clearly triaged issue with high-signal labels and, when needed, one short request for missing information.
- A routing decision that maintainers can audit without rereading the entire thread.

## Customization Notes
- Replace the category and priority labels with your repository's exact label set.
- If your team uses milestones or projects for triage, extend the instructions with your routing rules.
- Keep `safe-outputs` tight so this workflow can only label and leave one clarification comment.
