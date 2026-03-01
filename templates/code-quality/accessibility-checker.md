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

# Accessibility Checker

## Purpose
Review UI-facing changes for accessibility regressions that would block keyboard, screen reader, or low-vision users.

## Trigger
Run when a pull request changes forms, navigation, dialogs, interactive components, content structure, or visual status cues.

## Instructions
1. Inspect the changed UI markup, component props, labels, and interaction logic for likely accessibility regressions.
2. Focus on concrete risk areas: missing labels, broken semantics, inaccessible custom controls, focus traps, hidden state without announcements, color-only status cues, and invalid heading structure.
3. Distinguish visible refactors from behavior changes that would affect keyboard navigation or assistive technologies.
4. If the diff indicates a likely accessibility issue, use safe outputs to leave one concise comment naming the exact element and the missing accessibility requirement.
5. If the change looks acceptable but cannot be fully verified from code alone, note what would need manual UI testing instead of over-claiming certainty.
6. Avoid generic WCAG dumping; keep the review tied to the changed surface.
7. Prioritize issues that would block real usage over minor theoretical nits.

## Expected Output
- A focused accessibility finding tied to a specific changed interaction or element.
- Clear explanation of the user impact and the most practical remediation direction.

## Customization Notes
- Add repository-specific accessibility standards, component libraries, or design-system constraints.
- If your team has known a11y testing expectations, reference the most important ones.
- Keep comments limited to materially actionable accessibility risks.
