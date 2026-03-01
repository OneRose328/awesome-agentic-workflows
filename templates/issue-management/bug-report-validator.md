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

# Bug Report Validator

## Purpose
Check whether a bug report has the minimum evidence needed for reproduction, scoping, and reliable ownership assignment.

## Trigger
Run when a new or edited issue appears to report broken behavior and maintainers need to know if it is actionable or still missing core facts.

## Instructions
1. Decide whether the report is truly a defect report or is better treated as support, feature discussion, or an unsupported environment case.
2. Check for four minimum signals: what happened, what was expected, where it happened, and how someone could begin to reproduce it.
3. Look for confidence-raising evidence such as exact error text, logs, screenshots, version ranges, links to failing runs, or narrowed scope.
4. Identify the single missing detail that most blocks actionability right now. Prioritize the one fact that would change triage confidence the most.
5. Use safe outputs to add only the labels that change the next handling step, such as `bug`, `needs-repro`, `needs-version`, or `needs-logs`.
6. If the report is incomplete, ask for one concrete missing detail in plain language instead of dumping a whole checklist back at the reporter.
7. If the report is already actionable, say that it has enough detail for maintainer triage and avoid unnecessary follow-up.
8. If the evidence points to severe impact but the report is incomplete, call out both the risk signal and the missing blocking detail.

## Expected Output
- A clear judgment: actionable now, actionable after one detail, or not a bug report.
- One focused follow-up that makes the next maintainer step obvious.

## Customization Notes
- Replace the example labels with your actual intake states and severity taxonomy.
- Add product-specific requirements such as browser info, OS matrix, or build SHA when those are mandatory for debugging.
- Keep the missing-info request narrow so reporters can respond quickly.
