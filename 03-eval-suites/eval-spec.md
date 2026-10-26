Eval Spec · Misrepresented Native Integration (#HALLUCINATION), an output risk
| Part | Spec |
|---|---|
| Target risk | Misrepresented Native Integration (#HALLUCINATION), an output risk |
| Evaluator | The judge from Lab 1 |
| Threshold | Ship only if the evaluator catches 100% of confirmed integration-misrepresentation cases in the golden set (currently 2/2), with zero false alarms on audit-passing rows (currently 0/6). Any missed case blocks release. Supporting results: the rule check caught 1 of 2, the safety rule caught 1 of 2, the judge caught 2 of 2. |
| Business stakes | Misrepresented integration capabilities can lead enterprise clients to select unsuitable products, incur unexpected implementation costs, and delay projects—damaging trust in Ascend IQ and putting $50k+ annual renewals at risk. |
| Owner | The Ascend IQ Product Manager owns the quality threshold, monitors eval results, and signs off on release readiness. The Engineering Lead enforces the automated gate and blocks releases that fail it. |
