# Low-Token Optimization Workflow

This workflow is designed for repositories with mixed stacks (Dojo, Angular, Java) where you want high-quality optimization suggestions with minimal Copilot token usage.

## 1) Discover (small scope)

- Analyze one module or file at a time.
- Ask for architecture or hotspot hints only for the selected path.
- Avoid broad prompts like "optimize the whole repo".

Suggested prompt:

```text
Analyze ONLY <PATH>. Identify top 3 likely performance hotspots by impact and risk. Keep answer under 200 words.
```

## 2) Patch (targeted)

- Use the master prompt from `docs/copilot-optimization-master-prompt.md`.
- Constrain to one function or one file when possible.
- Request unified diff output only.

## 3) Validate (quick checks)

For each change, run only essential checks:

- Existing unit/integration tests touching the path
- Build/type-check for the modified module
- One runtime sanity check for behavior parity

## Guardrails

- Preserve behavior first; optimize second.
- Prefer low-risk high-impact changes before deeper refactors.
- Do not introduce new dependencies unless justified.
- If context is missing, ask for that exact file/function instead of guessing.

## Optional per-stack emphasis

- Java: allocations, collections, DB round-trips, thread safety
- Angular: `OnPush` suitability, template loops, recomputation, subscription lifecycle
- Dojo 1.x AMD: memory leaks, DOM churn, event cleanup; keep legacy-compatible syntax
