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

# First Response

## Purpose
Post a first maintainer response that acknowledges the report, sets a realistic next step, and reduces repetitive follow-up noise.

## Trigger
Run when a new issue arrives and maintainers want a timely, useful first reply before detailed triage happens.

## Instructions
1. Classify the issue into one of four first-response lanes: likely bug, likely feature request, likely support question, or likely duplicate candidate.
2. Reflect that lane in the reply so the author gets a response that matches the issue type instead of a generic acknowledgement.
3. Name the immediate next maintainer action, such as bug triage, feature review, docs pointer, duplicate search, or request for one missing detail.
4. Ask for at most one blocking detail in the first comment. Good examples are exact version, reproduction steps, failing command, or expected outcome.
5. Use safe outputs to apply only the labels that help intake routing right now; do not add cosmetic labels that do not change handling.
6. Keep the comment compact enough to read in one screen on mobile and structured enough that maintainers can reuse it without rewriting.
7. Avoid timelines, guarantees, or implied approval. The goal is clear intake, not false certainty.
8. If the issue appears abusive, security-sensitive, or likely to require private handling, avoid a detailed public exchange and defer to maintainers.

## Expected Output
- One first-touch reply that feels specific, calm, and operationally useful.
- Only the labels and expectation-setting needed to reduce repeated maintainer clarification work.

## Customization Notes
- Replace the tone and labels with your repository's actual contributor-facing norms.
- Add escalation rules for security reports, code-of-conduct issues, or enterprise customer intake if those exist.
- Keep the first comment short enough that maintainers will not need to rewrite it by hand.
