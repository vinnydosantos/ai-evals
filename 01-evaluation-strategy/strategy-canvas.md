# AI Evaluation Strategy Canvas

> Repo file `ai-evals/01-evaluation-strategy/strategy-canvas.md` (the repo is your submission).
> Becomes the **Strategy Canvas** slide of the final pitch deck you assemble in Module 6.
>
> Fill this with the **AI Evaluation Strategy Canvas** tool, then **Copy markdown** and paste it over this file. The headings below mirror the tool's output exactly.

## 1. Product Strategy, The Context

- **Target user:** VP-level Strategists and Product Leaders at Fortune 500 companies.
- **Key use case:** Ask plain-language market intelligence questions and receive clear, source-grounded comparisons and summaries.
- **Value proposition:** Help enterprise clients find trusted market insights faster to support informed business decisions.
- **Priority rationale:** Incorrect insights could mislead clients' decisions, so trustworthy information is the priority.

## 2. Measurements, The Execution

- **User promise.** For enterprise strategy and product leaders, Ascend IQ promises clear market insights grounded in verified sources so that they can make informed decisions faster and retain confidence in Ascend Analytics.
- **Top 3 trust metrics:**
  - **Hallucination Rate**, percentage of evaluated responses containing at least one false or fabricated factual claim, checked against verified sources. Protects clients from misleading business decisions.
  - **Robustness**, percentage of ambiguous, misleading, or out-of-scope test queries handled correctly through a grounded answer, clarification, or explicit limitation. Prevents confident answers when evidence is insufficient.
  - **Latency**, P95 elapsed time from submitting a query to receiving a complete response. Ensures trusted insights arrive quickly enough to improve the research experience.
- **Why these three:** Clients need reliable insights to avoid misguided decisions, appropriate handling of uncertain questions, and fast answers that reduce research time.

## 3. Strategic Trade-Offs, The Cost

### Trade-off 1 · Factual reliability ↔ Latency

We prioritize factual reliability over response speed because incorrect insights could mislead clients' business decisions. We accept longer response times when source verification is needed to avoid giving clients unreliable guidance.

### Trade-off 2 · Robustness ↔ Answer coverage

We prioritize robustness over answer coverage because a confident answer without sufficient evidence could mislead clients' decisions. We accept clarification requests or unanswered questions when evidence is insufficient, rather than providing unreliable guidance.

---
_Generated from the AI Evaluation Strategy Canvas, M1 lab tool, AI Evals Certification._
