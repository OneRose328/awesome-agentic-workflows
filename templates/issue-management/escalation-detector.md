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

# Escalation Detector

## Purpose
Identify issues that look urgent, incident-like, or severe enough to require faster maintainer escalation than normal triage.

## Trigger
Run when a new or updated issue suggests production impact, widespread breakage, security sensitivity, or business-critical disruption.

## Instructions
1. Read the issue for concrete urgency signals: outages, data loss, failed deployments, broken auth, payment impact, security exposure, or broad user disruption.
2. Distinguish truly urgent reports from emotionally worded but low-evidence complaints.
3. Identify the main escalation reason, such as severity, blast radius, customer impact, or security risk.
4. Use safe outputs to add up to three labels that accelerate routing, for example `urgent`, `incident-candidate`, `customer-impact`, or `needs-maintainer-now`.
5. If the report appears credible and actionable, leave one short comment that summarizes the escalation reason and requests prompt maintainer review.
6. If evidence is weak, state that urgency is unconfirmed and avoid labeling the issue as an incident without support.
7. Never disclose sensitive handling steps publicly for security-related reports.

## Expected Output
- A severity-oriented triage result that separates real escalation candidates from normal intake.
- One concise public signal that helps maintainers prioritize the issue correctly.

## Customization Notes
- Replace the sample labels with your incident, severity, or paging taxonomy.
- Add repository-specific definitions for what counts as P0, P1, or security-sensitive impact.
- Keep public wording calm and factual so urgent labels do not create unnecessary alarm.
