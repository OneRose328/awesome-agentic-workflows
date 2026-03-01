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

# API Consistency Checker

## Purpose
Review API-facing changes for consistency with existing contracts, naming, payload shape, and compatibility expectations.

## Trigger
Run when a pull request changes public endpoints, internal service contracts, request schemas, response fields, event payloads, or client-facing method names.

## Instructions
1. Inspect the changed API surface and compare it with existing patterns for naming, versioning, required fields, nullability, pagination, status codes, and error shape.
2. Flag contract drift such as inconsistent field names, surprising casing, mismatched enum semantics, changed defaults, or incompatible payload restructuring.
3. Distinguish harmless internal refactors from changes that would confuse callers or downstream tooling.
4. If a compatibility risk exists, use safe outputs to leave one concise comment naming the exact contract mismatch and the most likely fix.
5. If the diff suggests a breaking API change, state that explicitly so reviewers can decide whether versioning or migration notes are needed.
6. If the available context is too narrow to infer the established convention, say what reference surface is missing.
7. Focus on consumer-facing consistency, not general code style.

## Expected Output
- A focused contract review note that highlights a real API inconsistency or confirms the change is aligned.
- Clear explanation of why the inconsistency would matter to callers, clients, or future maintenance.

## Customization Notes
- Add repository-specific rules for versioning, compatibility guarantees, and schema evolution.
- If your project has canonical API style docs, align the review guidance with those rules.
- Keep comments limited to material contract drift, not minor wording preferences.
