# Copilot Optimization Master Prompt

Use this prompt template to get precise optimization suggestions with minimal token usage.

## Reusable master prompt

```text
You are optimizing code in repository: whsalazar-org/dojo-angular-optimization-copilot-demo.

Goal:
- Minimize token usage.
- Maximize correctness.
- Preserve behavior.

Scope (STRICT):
- Analyze ONLY: <PATH_OR_SNIPPET>
- If information is missing, state "insufficient context" instead of guessing.
- Do NOT analyze unrelated files/modules.

Tech constraints:
- Java: prioritize CPU, memory allocations, collection usage, and DB-call efficiency; preserve thread safety.
- Angular: prioritize render performance, change detection strategy, template efficiency, and avoiding recomputation.
- Dojo: code is legacy Dojo 1.x AMD; optimize without framework migration; keep valid Dojo 1.x patterns.

Output format (STRICT, concise):
1) "Findings" (max 3 bullets): highest-impact optimization opportunities only.
2) "Patch" (unified diff only, minimal lines changed).
3) "Risk" (one line): low/medium/high + why.
4) "Validation" (max 3 checks): how to verify no behavior regression.

Hard rules:
- No full-file rewrites.
- No new dependencies unless explicitly requested.
- No style-only refactors.
- Keep algorithmic complexity explicit when relevant.
- If confidence < 80%, say so briefly and request the exact missing file/function.
```

## Ultra-short variant: Java

```text
Optimize ONLY <PATH_OR_SNIPPET> for Java CPU/memory/collections/DB efficiency. Preserve behavior and thread safety. Return: top 3 findings, minimal unified diff, risk line, 3 validation checks. No new deps, no full-file rewrite.
```

## Ultra-short variant: Angular

```text
Optimize ONLY <PATH_OR_SNIPPET> for Angular render performance (change detection, template loops, recomputation). Preserve behavior. Return: top 3 findings, minimal unified diff, risk line, 3 validation checks. No new deps, no full-file rewrite.
```

## Ultra-short variant: Dojo 1.x

```text
Optimize ONLY <PATH_OR_SNIPPET> for Dojo 1.x AMD performance and memory. Keep Dojo 1.x AMD syntax; no framework migration. Return: top 3 findings, minimal unified diff, risk line, 3 validation checks. No new deps, no full-file rewrite.
```
