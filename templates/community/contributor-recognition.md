---
on:
  schedule: every 1mo
permissions:
  issues: read
  discussions: read
tools:
  github:
    toolsets: [issues, discussions]
network: defaults
safe-outputs:
  create-issue:
    max: 1
---

# Contributor Recognition

## Purpose
Highlights contributor wins and milestones in a way that feels specific, fair, and worth publishing.

## Trigger
Run on a recurring cadence to surface meaningful contributor wins, milestones, and sustained project support.

## Instructions
1. Review recent contribution activity across issues, pull requests, reviews, docs, and maintenance work.
2. Prioritize meaningful contribution signals: first merged contribution, sustained bug-fixing, unblocking release work, mentorship, docs improvements, triage help, or long-running maintenance effort.
3. Recognize contributions specifically. Name the work and why it mattered instead of posting generic praise.
4. Balance visibility across contribution types so only code authors do not get recognized.
5. Prefer a few high-signal acknowledgements over an exhaustive thank-you list that nobody reads.
6. Use safe outputs to create one recognition post or roundup issue for the current period.
7. If activity is low, keep the update short rather than forcing a “celebration” with weak signal.
8. Avoid over-rotating on vanity metrics; recognize impact, consistency, and community health.

## Expected Output
- A concise recognition summary that is specific, fair, and genuinely useful for community morale.
- A post maintainers can publish with minimal editing and without sounding generic.

## Customization Notes
- Define the cadence and the kinds of contributions your project wants to highlight most.
- If your community prefers quiet recognition, adapt the output for release notes or internal roundup instead of a public post.
- If your project has cultural norms around opt-in recognition, encode those boundaries here.
- Keep the output to one canonical roundup so recognition is easy to reference later.
