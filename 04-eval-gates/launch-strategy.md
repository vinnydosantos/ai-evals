# Module 4 · Launch Strategy · Ascend IQ Copilot

## 4.0 Release Criteria

| Gate | Failure | Metric | Threshold | Dataset | Method | Runs at |
|---|---|---|---|---|---|---|
| Hard | Misrepresented Native Integration (#HALLUCINATION) | Detection rate for confirmed integration-misrepresentation cases, alongside the false-alarm rate on audit-passing answers. | Ship only if the evaluator catches 100% of confirmed integration-misrepresentation cases in the golden set (currently 2/2), with zero false alarms on audit-passing rows (currently 0/6). Any missed case blocks release. | Ascend IQ golden set | LLM judge | Staging |
| Soft | Row 5 · Hallucination: lists an unconfirmed speaker as confirmed | Percentage of speaker-list answers that present invited or tentative speakers as confirmed. | 0%. Any occurrence pauses release pending a documented override. | Ascend IQ golden set | LLM judge | Staging |
| Advisory | Row 17 · Tone: slang detected | Percentage of cold-email drafts containing slang from the prohibited-phrase list. | 0%. Any occurrence triggers a warning without blocking release. | Ascend IQ golden set | Code-based check | Pull Request |

## CI Gate Request for Engineering

- **Hard gate · Misrepresented Native Integration (#HALLUCINATION).** Check: the LLM judge, run on the Ascend IQ golden set at Staging. Measures: Detection rate for confirmed integration-misrepresentation cases, alongside the false-alarm rate on audit-passing answers.. Passes when: Ship only if the evaluator catches 100% of confirmed integration-misrepresentation cases in the golden set (currently 2/2), with zero false alarms on audit-passing rows (currently 0/6). Any missed case blocks release.. On a fail: block the merge.
- **Soft gate · Row 5 · Hallucination: lists an unconfirmed speaker as confirmed.** Check: the LLM judge, run on the Ascend IQ golden set at Staging. Measures: Percentage of speaker-list answers that present invited or tentative speakers as confirmed.. Passes when: 0%. Any occurrence pauses release pending a documented override.. On a fail: pause the release until the PM signs off on an override.
- **Advisory gate · Row 17 · Tone: slang detected.** Check: the code-based check, run on the Ascend IQ golden set at Pull Request. Measures: Percentage of cold-email drafts containing slang from the prohibited-phrase list.. Passes when: 0%. Any occurrence triggers a warning without blocking release.. On a fail: post a warning, and don't block.

## Mitigation Plan · Soft Gate

f our Soft gate fails because invited speakers are presented as confirmed, we will use a feature flag to disable speaker-confirmation answers while releasing the rest of Ascend IQ under a documented PM override. This lets us collect failed cases, expand the golden set, and re-enable the capability after it meets the 0% error threshold.
