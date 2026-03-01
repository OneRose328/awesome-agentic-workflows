---
on:
  issues:
    types: [opened]
permissions:
  issues: read
  discussions: read
tools:
  github:
    toolsets: [issues, discussions]
network: defaults
safe-outputs:
  add-comment:
    max: 1
---

# New Contributor Welcome

## Purpose
Welcome first-time contributors with the minimum guidance they need to make a good next move.

## Trigger
Run when a new issue is opened. Use the instructions to distinguish first-time contributors from returning ones — only welcome users whose first interaction with this repository is the issue being opened. To also welcome first-time pull request authors, add `pull_request_target: [opened]` to the `on:` block and extend the instructions accordingly.

## Instructions
1. Confirm the contributor appears new to the repository and the interaction is suitable for a welcome message.
2. Tailor the welcome to the actual context: issue report, pull request, question, or documentation contribution.
3. Point them to the next best resource, such as contribution guidelines, setup docs, issue labels, or discussion norms.
4. Use safe outputs to post one short welcome comment that is friendly but not overlong.
5. Avoid repeating guidance they already followed correctly.
6. If the interaction is frustrated or tense, keep the reply grounded and useful rather than overly cheerful.
7. Do not make promises about review speed or acceptance.

## Expected Output
- A concise welcome note that helps new contributors orient quickly.
- Lower friction for first-time contributors without adding comment spam.

## Customization Notes
- Replace the sample pointers with your actual contributor guide, setup docs, and support channels.
- Tune the tone to match your community norms and maintainer voice.
- Keep the message brief enough that repeat contributors are not flooded with boilerplate.
