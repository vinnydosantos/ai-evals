# AI Evaluation Strategy Canvas

> Repo file `ai-evals/01-evaluation-strategy/strategy-canvas.md` (the repo is your submission).

## 1. Product Strategy, The Context

**Who it's for:** VP-level strategists and product leaders at Fortune 500 companies who pay upward of $50,000 a year for verified market intelligence.

**What they use it for:** Asking plain-language questions, like “Compare the pricing models of Stripe and Adyen,” and getting answers in seconds instead of digging through the platform.

**What's at stake:** Engagement is dropping, Q4 retention is at risk, and the CPO wants Ascend IQ live for the top 50 enterprise accounts next month. One poor answer to the wrong client can do lasting damage to the relationship.

## 2. Measurements, The Execution

**User promise.** For VP-level strategists and product leaders, Ascend IQ promises to deliver accurate market insights in seconds, backed by verified sources, so that they can make informed decisions faster and confidently rely on Ascend Analytics.

**Top 3 trust metrics:**
- **Latency**, Response speed (P95 / P99). Slow kills engagement.
- **Hallucination Rate**, % of outputs that are confidently false or fabricated.
- **Robustness**, Coherence on messy, adversarial, out-of-scope inputs.

**Why these three:** Hallucination Rate: Supports “accurate insights backed by verified sources” by measuring false or fabricated claims that could mislead decisions.
Latency: Supports “deliver insights in seconds” by measuring how quickly users receive a complete answer.
Robustness: Supports “confidently rely on Ascend Analytics” by checking that unclear or challenging questions lead to grounded answers, clarification, or explicit limitations.

## 3. Strategic Trade-Offs, The Cost

### Trade-off 1 · Hallucination Rate ↔ Latency
We prioritize reducing hallucination rate over minimizing latency because clients rely on Ascend IQ for important business decisions, and a slower, verified answer is preferable to a fast, misleading one.

### Trade-off 2 · Latency ↔ Robustness
We prioritize robustness over minimizing latency because clients need reliable handling of ambiguous or challenging questions, even when validation, retries, or clarification take additional time.

---
_Generated from the AI Evaluation Strategy Canvas, M1 lab tool, AI Evals Certification._
