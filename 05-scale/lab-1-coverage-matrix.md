# Module 5 · Coverage Matrix · AI Report Summaries

## Coverage Row

| Product | Hallucination Rate | Fairness | Latency | UX Trust | Robustness |
|---|---|---|---|---|---|
| AI Report Summaries | ✅ Covered | ❌ Gap | ⚠️ Partial | ❌ Gap | ❌ Gap |

## What Runs Today

- An LLM judge compares each summary with its source report before every release.
- Response time is logged, but nobody has set a target.

## Accepted Gap

**UX Trust.** Tone issues pose less immediate risk to clients’ business decisions than factual errors or failures to handle complex reports, so we prioritize those risks before funding a dedicated tone evaluator.

We’ll look again: We will add a tone evaluator if a client complaint or account-manager escalation identifies wording that undermines confidence in a summary. We will review this decision in 30 days, even if no concerns are reported.

## Critical Gap

We’ve flagged Robustness as the most critical gap for AI Report Summaries because 

## After the Pressure Test

I kept the coverage marks but strengthened the plan: add weekly reviews of live summaries alongside the pre-release robustness gate, assign an owner, and define blocking failures. I also added proactive tone spot-checks during the 30-day acceptance period rather than relying only on client complaints.
