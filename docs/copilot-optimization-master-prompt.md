# Copilot Optimization Master Prompt

Use this prompt template to get precise optimization suggestions with efficient token usage and focused context.

## Reusable master prompt

```text
You are optimizing code in repository: whsalazar-org/dojo-angular-optimization-copilot-demo.

Goal:
- Use efficient token usage and focused context.
- Maximize correctness.
- Preserve functionality contracts.
- Treat token usage and accuracy as a trade-off: add relevant context when it improves accuracy, but avoid irrelevant files or instructions.

Scope (STRICT):
- Analyze primarily: <PATH_OR_SNIPPET>
- Expand to directly related callers, callees, or types only when needed to avoid incorrect assumptions.
- If information is missing, state "insufficient context" instead of guessing.
- Ask for more relevant context when it would improve accuracy; do not pull in unrelated files/modules.
- Do NOT analyze unrelated files/modules.

Tech constraints:
- Java: prioritize CPU, memory allocations, collection usage, and DB-call efficiency; preserve thread safety.
- Angular: prioritize render performance, change detection strategy, template efficiency, and avoiding recomputation.
- Dojo: code is legacy Dojo 1.x AMD; optimize without framework migration; keep valid Dojo 1.x patterns.

Output format (STRICT, concise):
1) "Findings" (max 3 bullets): highest-impact optimization opportunities only.
2) "Patch" (unified diff only, minimal lines changed).
3) "Risk" (one line): low/medium/high + why.
4) "Complexity impact" (max 3 bullets): note meaningful complexity changes, or say unchanged.
5) "Validation" (max 3 checks): define what to measure, how to verify functionality contracts, and compare with actual before/after metrics.

Hard rules:
- No full-file rewrites.
- No new dependencies unless explicitly requested.
- No style-only refactors.
- Keep algorithmic complexity explicit when relevant.
- If confidence < 80%, say so briefly and request the exact missing file/function.
```

## Ultra-short variant: Java

```text
Optimize primarily <PATH_OR_SNIPPET> for Java CPU/memory/collections/DB efficiency. Expand only to directly related callers/callees/types when needed. Preserve functionality contracts and thread safety. Return: top 3 findings, minimal unified diff, risk line, 3 complexity bullets, 3 validation checks with real measurements. No new deps, no full-file rewrite.
```

## Ultra-short variant: Angular

```text
Optimize primarily <PATH_OR_SNIPPET> for Angular render performance (change detection, template loops, recomputation). Expand only to directly related callers/callees/types when needed. Preserve functionality contracts. Return: top 3 findings, minimal unified diff, risk line, 3 complexity bullets, 3 validation checks with real measurements. No new deps, no full-file rewrite.
```

## Ultra-short variant: Dojo 1.x

```text
Optimize primarily <PATH_OR_SNIPPET> for Dojo 1.x AMD performance and memory. Expand only to directly related callers/callees/types when needed. Keep Dojo 1.x AMD syntax; no framework migration; preserve functionality contracts. Return: top 3 findings, minimal unified diff, risk line, 3 complexity bullets, 3 validation checks with real measurements. No new deps, no full-file rewrite.
```
