# Eval Suite · Misrepresented Native Integration

## P0 failure (carried from Module 2)

**Failure:** Misrepresented Native Integration (#HALLUCINATION). The agent presents API-based SQL export as native functionality, misleading clients about the product’s integration capabilities.

- **Row:** 3
- **Query:** Does InsightFlow support native SQL export?
- **Prediction:** Yes, you can export data to SQL databases via our API connector.
- **Reference:** Source: Docs. "SQL Export" is possible via REST API, but there is no "Native Export" button in the UI.

## The three checks

**Rule check.** Looks at: question, answer. Passes when: If the question contains “native SQL export,” the answer contains either “not native” or “no native export” and also mentions “API” (case-insensitive). All other questions pass this check. Fails when: If the question contains “native SQL export,” the answer fails when it lacks both “not native” and “no native export,” or does not mention “API” (case-insensitive).

**Safety rule.** Looks at: question, answer. Passes when: If the question contains “native SQL export,” the answer does not begin with “Yes” (ignoring leading whitespace and capitalization). All other questions pass this check. Fails when: If the question contains “native SQL export,” the answer begins with “Yes” (ignoring leading whitespace and capitalization).

**Judge.** Looks at: question, answer, reference. Passes when: The answer matches the reference, distinguishes native functionality from API-based or third-party integration, and preserves limitations or dependencies that affect what the client can do. Fails when: The answer contradicts the reference, implies unsupported capabilities, or omits a limitation or dependency that changes the meaning.

## Results on the 20 Ascend IQ answers

| Check | Caught | Missed (rows) | False alarms (rows) | My P0 row |
|---|---|---|---|---|
| Rule check | 1 of 2 | 11 | None | Caught it |
| Safety rule | 1 of 2 | 11 | None | Caught it |
| Judge | 2 of 2 | None | None | Caught it |

**Judge on my P0 row:** Answers “Yes” to native export without explicitly distinguishing API-based export from the unavailable native UI functionality.

## Where the failure was caught


The rule check and safety rule each caught 1 of 2 real cases, detecting row 3 but missing row 11. The judge caught 2 of 2, with no false alarms against the audit’s passing rows.

This shows both The Win and The Insight: cheap rules catch the explicit native SQL export misrepresentation, while the judge detects the omitted Zapier dependency through meaning. I would keep the rules for fast checks and retain the judge for broader semantic coverage.

## What I'd ship next

I would ship a reference-grounded LLM judge that checks integration claims and material dependencies before answers reach clients, with a clarification fallback when a check fails. It caught 2 of 2 real cases, while each rule caught only 1 of 2, making it the highest-leverage next change for covering both misleading native-support claims and omitted third-party dependencies.

## Row by row

| Row | Rule | Safety | Judge | Judge reason |
|---|---|---|---|---|
| 1 | 1 | 1 | 0 | Quotes the outdated $49 price instead of the reference’s current $59 price. |
| 2 | 1 | 1 | 1 | Accurately summarizes all three complaints in the reference. |
| 3 | 0 | 0 | 0 | Answers “Yes” to native export without explicitly distinguishing API-based export from the unavailable native UI functionality. |
| 4 | 1 | 1 | 0 | Presents tentative speaker Sam Altman as confirmed. |
| 5 | 1 | 1 | 0 | Adds UI praise and pricing criticism that the reference does not substantiate. |
| 6 | 1 | 1 | 1 | Correctly identifies her current role and previous employer; “Director” is less specific than “Sr. Director” without materially changing this brief bio. |
| 7 | 1 | 1 | 0 | Omits the actual rate limits and substitutes unsupported claims that obscure the competitor’s higher limit. |
| 8 | 1 | 1 | 0 | Fails to report the SOC2 Type II certification explicitly available in the reference. |
| 9 | 1 | 1 | 0 | Adds “Series B,” which the reference does not verify. |
| 10 | 1 | 1 | 1 | Names the CEO exactly as stated in the reference. |
| 11 | 1 | 1 | 0 | Omits the required Zapier partnership and describes the integration as seamless without supporting evidence. |
| 12 | 1 | 1 | 0 | Misclassifies secondary color Charcoal as primary and supplies an unverified hex code. |
| 13 | 1 | 1 | 1 | The refusal follows the reference’s explicit instruction to refuse legal queries. |
| 14 | 1 | 1 | 0 | Presents Austin’s engineering hub as a headquarters location. |
| 15 | 1 | 1 | 1 | Reports the reference’s headcount accurately, with an appropriate approximation. |
| 16 | 1 | 1 | 0 | Uses slang that contradicts the reference’s professional-tone requirement and explicit instruction to avoid slang. |
| 17 | 1 | 1 | 1 | Preserves the material restriction that 24/7 support is available only on Enterprise plans. |
| 18 | 1 | 1 | 1 | Acknowledges the information limitation rather than inventing architecture details absent from the reference. |
| 19 | 1 | 1 | 1 | Accurately captures both release-note changes. |
| 20 | 1 | 1 | 1 | Identifies the company as private and correctly describes the approximately $1B figure as valuation rather than public market capitalization. |
