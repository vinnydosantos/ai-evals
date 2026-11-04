# Module 5 · Eval Budget · Ascend IQ

**Quarterly budget cap:** $200,000
**Online eval spend:** $85,000 (1 of at most 3 online evals)

## Budget

| Failure | Trust metric | Risk | Level | Cost |
| --- | --- | :---: | :---: | ---: |
| Data Fabrication | Hallucination Rate | P0 | Online eval | $85,000 |
| Context Specificity | Robustness | P1 | Periodic audit | $7,000 |
| Overconfident Tone | UX Trust | P1 | Periodic audit | $6,500 |
| Data Bias | Fairness | P2 | Periodic audit | $5,500 |
| Slow Answers | Latency | P3 | Code-based check | $1,250 |

## Downgrades

### Periodic audit · Context Specificity (Robustness · P1)
- **Cheaper check:** eekly human review of live answers against the exact request, sampling queries with constraints such as “negative reviews only
- **Why it’s enough:** Human review can detect missed intent that simple rules overlook, at 10% of the online cost. We accept the delay between audits temporarily and reconsider online coverage if repeated or decision-critical failures appear.

### Periodic audit · Overconfident Tone (UX Trust · P1)
- **Cheaper check:** Weekly human review comparing claims with their sources, flagging guesses presented as facts or omitted uncertainty.
- **Why it’s enough:** Source-based review can assess whether confidence is justified; keyword checks cannot. This accepts a detection delay to preserve budget for higher-impact risks. Escalate to online evaluation if repeated failures influence client decisions.

### Periodic audit · Data Bias (Fairness · P2)
- **Cheaper check:** Weekly human review of a sample balanced across US and APAC queries, comparing source coverage and omitted regional findings.
- **Why it’s enough:** A regional audit can detect systematic US favoritism at 10% of the online cost. We accept the detection delay for this P2 risk and escalate if APAC quality repeatedly falls below US quality or clients report material omissions.

### Code-based check · Slow Answers (Latency · P3)
- **Cheaper check:** Before every release, time a fixed set of long, multi-step queries and flag responses exceeding 10 seconds.
- **Why it’s enough:** Latency is directly measurable without an LLM judge. This cheaply catches release regressions; we accept that release-only testing can miss production slowdowns.

