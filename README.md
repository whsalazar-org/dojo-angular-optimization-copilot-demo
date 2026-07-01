# dojo-angular-optimization-copilot-demo

## GitHub Copilot strategy: optimize with low tokens + high accuracy

Use this workflow when improving a Dojo/Angular frontend with a Java backend:

1. **Narrow scope first**
   - Ask Copilot to focus on one module, endpoint, or component at a time.
   - Provide exact files/paths and expected outcome.

2. **Give structured context**
   - Include architecture notes: Dojo widgets/services, Angular modules/components, Java controllers/services/repositories.
   - Share constraints (performance budget, API contracts, coding standards, target Java/Angular versions).

3. **Use a token-efficient prompt template**
   - _“Analyze only `<file paths>`. Find top 3 performance bottlenecks. Propose minimal diff with no behavior changes. Explain complexity impact in 3 bullets.”_

4. **Prefer iterative changes**
   - Request one small patch, review it, run tests, then continue.
   - Avoid “rewrite everything” prompts.

5. **Anchor Copilot to measurable goals**
   - Frontend: render time, bundle size, change detection cost.
   - Backend: query count, response time, memory allocation, thread/connection usage.

6. **Require evidence in responses**
   - Ask Copilot to cite exact lines and estimate before/after impact.
   - Request edge cases and regression risks for each proposed change.

7. **Validate every step**
   - Run existing lint/build/test commands after each patch.
   - Keep only improvements that preserve correctness and improve target metrics.

### Recommended prompt sequence

1. **Discovery**
   - _“Read only `<paths>`. Summarize current hotspots and why they are expensive.”_
2. **Plan**
   - _“Provide 2-3 minimal optimization options ranked by impact/risk.”_
3. **Patch**
   - _“Implement option #1 as a minimal diff. No unrelated refactors.”_
4. **Verification**
   - _“List test cases and metrics to validate this change.”_

This approach minimizes tokens (small scope, short iterative prompts) while improving accuracy (explicit context, measurable goals, strict validation).
