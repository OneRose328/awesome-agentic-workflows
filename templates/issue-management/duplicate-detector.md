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
  add-comment:
    max: 1
  update-issue:
---

# Duplicate Detector

## Purpose
Flags likely duplicate issues and links maintainers to the matching thread.

## Trigger
Run when a new issue is opened or when a heavily edited issue now appears to overlap with an existing report.

## Instructions
1. Read the new issue carefully: title, body, stack traces, reproduction steps, environment details, and any component names.
2. Compare it against likely overlapping issues using concrete similarity signals such as identical errors, same subsystem, same user-facing symptom, or matching regression window.
3. Prefer high-confidence duplicates only. Similar wording alone is not enough if the reproduction or impact differs.
4. If a likely duplicate exists, use safe outputs to leave one comment linking the closest matching issue and explain the overlap in one or two concrete points.
5. If your workflow policy allows it, update the issue only when the duplicate signal is strong enough that a maintainer would likely make the same call.
6. If confidence is low, note that a related issue may exist but avoid collapsing distinct reports into one thread.
7. Keep the workflow focused on de-duplication, not on full triage or resolution.

## Expected Output
- A high-confidence duplicate signal that helps maintainers consolidate discussion without closing distinct issues by mistake.
- Clear explanation of why the linked thread appears to match.

## Customization Notes
- Add any repository-specific duplicate heuristics, such as label matches, subsystem tags, or issue-form fields.
- Keep duplicate handling conservative if your project often has similar symptoms caused by different root causes.
- If maintainers prefer manual closure, keep this workflow limited to comments and skip automatic issue updates.
