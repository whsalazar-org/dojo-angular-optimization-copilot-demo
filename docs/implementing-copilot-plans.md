# Implementing Code Changes After a Copilot Plan

This guide explains the safest, lowest-noise way to execute code changes after Copilot drafts a plan, and where to keep those plans in this repository.

## Where to keep plans

Use a consistent location so plans are easy to find and review:

- Folder: `docs/plans/`
- File naming: `YYYY-MM-DD-<short-topic>.md`
  - Example: `2026-07-01-angular-table-render-optimization.md`

Recommended plan template sections:

1. **Context** (feature/module and constraints)
2. **Goal** (measurable target)
3. **Scope** (files/functions included + explicitly excluded)
4. **Proposed Changes** (small, ordered steps)
5. **Risk & Rollback** (what could break, how to revert)
6. **Validation** (tests/checks to run)
7. **Result** (what changed + metrics if available)

---

## Best implementation workflow

After Copilot provides a plan, execute in small, verifiable steps.

### 1) Convert plan into small tasks

Break the plan into 1–3 file changes per task.

- Prefer one hotspot at a time.
- Keep each commit focused and reversible.

### 2) Pin exact scope in prompts

When asking Copilot for edits, include controlled scope:

- exact file path
- exact function/class
- constraints (no new deps, do not break functionality contracts)
- allow limited adjacent context only when needed (for example callers, callees, or related types)

### 3) Apply minimal diffs

Ask for unified diffs or minimal patches instead of full-file rewrites.

### 4) Validate immediately

For each task/commit, run only essential checks first:

- relevant unit/integration tests
- build/type-check for changed module
- one runtime sanity check
- before/after measurements for the selected metric

Ask Copilot what to measure before and after the change; do not rely on fabricated impact estimates.

### 5) Commit in narrow increments

Commit after each validated step using descriptive messages.

Examples:

- `perf(java): reduce allocations in UserService lookup path`
- `perf(angular): avoid template recomputation in table component`
- `perf(dojo): cleanup widget event handlers to prevent leaks`

### 6) Update the plan file with outcomes

After each commit, append:

- what was changed
- test/build status
- observed impact with actual before/after metrics (if measured)
- follow-up tasks

---

## Suggested repository conventions

- Keep planning docs in `docs/plans/`.
- Keep reusable prompt templates in `docs/`.
- Link commits/PRs back to the plan filename in descriptions.
- If a plan changes significantly, create a new dated plan file rather than overwriting history.

---

## Optional: quick starter plan template

```markdown
# <Title>

## Context

## Goal

## Scope
- Include:
- Exclude:

## Proposed Changes
1.
2.
3.

## Risk & Rollback

## Validation
- Tests:
- Build/type-check:
- Runtime sanity:
- Metrics to capture:

## Results
- Commits:
- Impact (measured):
- Follow-ups:
```
