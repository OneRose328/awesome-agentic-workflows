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

# Feature Request Analyzer

## Purpose
Triage a feature request into a clear next state by scoring user impact, scope, and missing product context.

## Trigger
Run when a new or edited issue appears to be a feature request and maintainers need to decide whether to scope it, request clarification, or park it.

## Instructions
1. Confirm the issue describes a requested capability rather than a bug report, support request, or roadmap status question.
2. Extract the core user problem, the proposed outcome, and any stated workaround so maintainers can judge demand versus implementation cost.
3. Check labels, linked issues, and nearby requests for duplicates, roadmap overlap, or signs that the request already exists under another name.
4. Identify the main blocker to triage: missing use case, unclear success criteria, broad scope, dependency risk, or likely duplicate.
5. Use safe outputs to add no more than three decision-driving labels such as `needs-scope`, `needs-design`, `needs-feedback`, or `duplicate-candidate`.
6. If the request is actionable but underspecified, leave one concise comment asking for the smallest missing product detail that would unblock prioritization.
7. If the request is clear and bounded, state the best next lane for maintainers: backlog candidate, needs product review, or needs technical spike.

## Expected Output
- A triage-ready view of the request's value, scope, and decision blocker.
- Labels and one focused maintainer note that move the request into the correct backlog lane.

## Customization Notes
- Replace the sample decision labels with your real intake states and product ownership tags.
- Add repository-specific rules for what counts as roadmap-worthy, partner-only, or out-of-scope work.
- Keep the follow-up comment prompt short so users are asked for one blocking detail, not a full rewrite.
