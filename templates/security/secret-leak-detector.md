---
on:
  workflow_dispatch: {}
permissions:
  contents: read
  issues: read
  pull-requests: read
  security-events: read
tools:
  github:
    toolsets: [repos, issues, pull_requests, code_security]
network: defaults
safe-outputs:
  add-comment:
    max: 1
---

# Secret Leak Detector

## Purpose
Flags possible credential leaks in diffs or repository content.

## Trigger
Run when a suspicious diff, pasted token, credentials file, or high-entropy secret-like value appears in review scope.

## Instructions
1. Inspect added lines, changed files, and filenames for secret-like material: API keys, tokens, private keys, connection strings, `.env` values, CI credentials, or copied cloud secrets.
2. Distinguish real exposure risk from harmless examples, test fixtures, redacted placeholders, or obviously fake sample values.
3. Never repeat or quote the secret value in output. Refer only to the file path, line context, and credential type.
4. If the signal is strong, use safe outputs to leave one urgent comment instructing the contributor to rotate the credential, remove it from history, and replace it with a secret manager or encrypted secret.
5. If the signal is weak, ask for manual security review instead of asserting a leak.
6. If the exposure appears to be in generated artifacts or vendored files, call out the likely source so maintainers can fix the root cause.
7. Treat this workflow as high-sensitivity: minimize noise, maximize clarity, and avoid public speculation beyond the immediate remediation step.

## Expected Output
- A clear, security-safe warning when a likely credential leak is present.
- No verbatim secret disclosure in comments or summaries.

## Customization Notes
- Add repository-specific secret patterns if your team uses known token prefixes or config file conventions.
- Keep this workflow limited to one short comment so it does not amplify a sensitive incident in public.
- If your project has a private disclosure process, point the workflow at that channel in the remediation message.
