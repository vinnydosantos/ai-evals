# First LLM-as-a-Judge Eval, Module 1

> Repo file `ai-evals/01-evaluation-strategy/eval-harness-proof.md`. The eval evidence behind the **Eval Results** slide of the final pitch deck (Module 6).
>
> Fill this with the **First Eval Lab** builder, then **Copy markdown** and paste it over this file. The headings below mirror the tool's output exactly.

## Version A, Concise, system prompt used

You are an executive briefing assistant. Summarize in exactly 3 bullet points under 60 words. No preamble, no extra text.

## Version B, Narrative, system prompt used

You are a PR communications assistant. Write a 100-word narrative summary highlighting wins first, then risks and next steps. Keep a positive tone. No bullets.

## Eval setup, dataset name + judge model/family

- **Dataset:** `Module1Output` — 20 synthetic email-summary examples; 10 provisional good labels and 10 provisional bad labels.
- **Generator:** ChatGPT (OpenAI family), used for both prompt versions.
- **Planned judge:** Claude (Anthropic family), different from the generator family to reduce self-preference bias.
- **Evaluator:** Conciseness; 1 = concise and faithful, 0 = not.
- **Status:** Optional cross-family judge scoring has not been run. Version A's previously recorded score of 1 is provisional, not a Claude judge result.
- **Scope:** This email-summary exercise demonstrates prompt comparison; it is not an evaluation of Ascend IQ's market-intelligence performance.
- **Human curation:** The learner accepted all 20 labels as a batch based on AI-assisted assessment against the learner's rubric, and specifically discussed row 14's redundancy. This was not an individual human review of every row. The dataset remains a starter set, not a fully validated golden dataset.

## Cold-start, the prompt you used to seed a starter dataset

Generate 20 example rows for evaluating email-summary quality. Each row: an input email + a candidate summary + a first-pass label ("good" or "bad") + a one-line reason. Make roughly half concise/faithful ("good") and half verbose or inaccurate ("bad"). Return it as a markdown table.

### Starter dataset

| # | Input email | Candidate summary | First-pass label | One-line reason |
|---|---|---|---|---|
| 1 | Social engagement rose 25% month-over-month. Newsletter open rate fell from 42% to 35%. We will test new subject lines next week. | Social engagement rose 25%; newsletter opens fell from 42% to 35%. Subject-line tests begin next week. | good | Concise and preserves the results and next step. |
| 2 | Revenue reached $1.2M against a $1.5M target. Finance will review the shortfall on Tuesday. | Revenue exceeded its target by $300K. Finance will review results Tuesday. | bad | Reverses the result: revenue missed the target by $300K. |
| 3 | The product launch moves from October 15 to November 2 because security testing is incomplete. Marketing should pause scheduled launch emails. | Launch postponed to November 2 due to incomplete security testing; Marketing must pause launch emails. | good | Preserves the revised date, blocker, and required action. |
| 4 | Legal has not approved the vendor contract. Procurement must wait before issuing the purchase order. | Legal approved the vendor contract; Procurement can issue the purchase order. | bad | Reverses approval status and authorizes a prohibited action. |
| 5 | Yesterday’s outage lasted 18 minutes and affected EU customers. Service is restored. Root-cause analysis is due Friday. | EU service is restored after an 18-minute outage; root-cause analysis is due Friday. | good | Accurately captures impact, recovery, and follow-up deadline. |
| 6 | We interviewed eight pilot users. Six found onboarding confusing. These findings may not represent our full customer base. | Most customers find onboarding confusing. | bad | Generalizes a small pilot sample and drops the stated limitation. |
| 7 | Please approve the $8,000 research budget by Thursday so recruiting can begin Monday. | Approval needed by Thursday for an $8,000 research budget to start recruiting Monday. | good | Retains the decision, amount, deadline, and dependency. |
| 8 | The beta is planned for Monday, provided QA signs off Friday. Two critical defects remain open. | The beta will launch Monday. | bad | Presents a conditional plan as certain and omits critical defects. |
| 9 | The supplier expects delivery between May 10 and May 12. This is an estimate, not a confirmed date. Operations will confirm tomorrow. | Estimated delivery is May 10–12; Operations will confirm tomorrow. | good | Preserves uncertainty and the confirmation step. |
| 10 | Customer churn increased from 4% to 6% this quarter. The team is investigating the causes. | Customer churn increased by 2% because support response times worsened. | bad | Confuses percentage points with percent change and invents a cause. |
| 11 | Effective immediately, stop using pricing sheet v3. Version 4 corrects enterprise pricing errors and is available in the shared folder. | Stop using pricing sheet v3 immediately; use v4 from the shared folder to avoid enterprise pricing errors. | good | Clearly preserves the urgent instruction and replacement source. |
| 12 | The customer renewed for one year at the existing price. They declined the proposed analytics add-on. | The customer renewed and purchased the analytics add-on. | bad | Invents an add-on purchase that the customer explicitly declined. |
| 13 | No customer data was exposed in the incident. Internal logs were accessible for 12 minutes. Security closed access and is reviewing controls. | No customer data was exposed; internal logs were accessible for 12 minutes. Access is closed, and Security is reviewing controls. | good | Distinguishes the actual exposure from customer-data impact. |
| 14 | Friday’s workshop is canceled. Ana will send a replacement date next week. | Regarding the workshop previously scheduled for Friday, the update is that it will no longer take place on that day because it has been canceled. Looking ahead to the coming week, Ana will communicate another update containing the replacement date for the workshop. | bad | Repeats two simple facts with unnecessary wording. |
| 15 | Support backlog fell from 120 to 75 tickets. Four urgent tickets remain; owners must post recovery plans by 3 p.m. today. | Support backlog fell to 75 from 120; four urgent tickets still require owner recovery plans by 3 p.m. today. | good | Balances progress with the remaining risk and deadline. |
| 16 | The campaign generated 400 leads. We have not yet measured how many converted into paying customers. | The campaign acquired 400 paying customers. | bad | Incorrectly equates leads with paying customers. |
| 17 | Correction to my earlier email: the board review is Wednesday at 10 a.m., not Tuesday. The meeting link is unchanged. | Board review is Wednesday at 10 a.m.; the meeting link is unchanged. | good | Uses the corrected schedule and preserves relevant logistics. |
| 18 | Maya owns the migration plan, due June 8. Leo will review it by June 10. | Leo must complete the migration plan by June 8; Maya will review it June 10. | bad | Swaps the accountable owner and reviewer. |
| 19 | The pilot reduced average handling time by 15%, but satisfaction scores were unchanged. We recommend extending the pilot before deciding on rollout. | Pilot handling time fell 15%; satisfaction was unchanged. Recommendation: extend the pilot before a rollout decision. | good | Preserves mixed results and distinguishes a recommendation from approval. |
| 20 | The security audit found three critical vulnerabilities. Release is blocked until all three are fixed and retested. Documentation updates are complete. | Documentation updates are complete, and the release is ready. | bad | Omits critical vulnerabilities and falsely declares release readiness. |

These are **AI-generated first-pass labels accepted by the learner as a batch with AI assistance**. Row 14 was specifically discussed. This starter set is not a fully validated golden dataset.


## Your definition of good vs bad (golden-set criteria) — the graded part, write your own

**Quality bar: Decision-ready CEO summaries.**

**My rationale:** The CEO is busy and handles many topics every day. They must be well and timely informed to make the right decisions.

**Good:** A summary is concise, faithful to the email, and easy to scan. It preserves decision-relevant results, risks, blockers, actions, and deadlines, including important uncertainty. It avoids repetition and unnecessary detail.

**Bad:** A summary invents or distorts facts, numbers, dates, owners, or approval status; omits decision-critical risks or actions; turns uncertainty into certainty; or uses unnecessary wording that makes the CEO work harder to find the main point.

**Format:** Exactly three bullets and fewer than 60 words are Version A instruction-compliance checks, not universal requirements for every starter example. Quality is judged by usefulness for the CEO as well as fidelity and conciseness.

**Scoring:** 1 = concise and faithful, preserving decision-critical information; 0 = fails one or more of those criteria. The learner accepted the starter labels as a batch with AI assistance; individual human review and full golden-set validation have not been performed.

## Screenshots, links or repo paths (optional if you followed the demo)

The following outputs were generated in this ChatGPT conversation using the same Q4 email. Instructions were supplied as chat messages, rather than through a separate system-prompt field. No API key or notebook was used.

### Input email

Subject: Q4 Marketing Campaign Update

Hi team,

Social media engagement is up 25% month-over-month due to the new content calendar and paid ad experiments.

Newsletter open rate dropped from 42% to 35%; we'll test new subject lines next week.

The product video campaign is delayed until November, pending legal approval; creative assets are ready.

Please ensure all campaign tracking links are added by Friday.

Best,
Priya

### Captured output A

- Social engagement increased 25% month-over-month, driven by the new content calendar and paid ad experiments.
- Newsletter open rate dropped from 42% to 35%; subject-line tests begin next week.
- Product video campaign delayed until November pending legal approval; creative assets are ready. All campaign tracking links are due Friday.

### Captured output B

Social media engagement climbed 25% month-over-month, driven by the new content calendar and paid advertising experiments. Creative assets for the product video campaign are also ready, positioning the team to proceed once legal approval arrives. The campaign is now delayed until November, making legal clearance a key dependency. Meanwhile, newsletter open rates declined from 42% to 35%, presenting an opportunity to improve audience engagement through new subject lines next week. To support campaign measurement, all tracking links must be added by Friday. The immediate priorities are testing newsletter improvements, securing legal approval, and completing tracking setup while sustaining social momentum.

### Comparison status

**Selected winner: Version A**, chosen by the learner for the CEO briefing. Its scannable bullets fit the learner's stated rationale: a busy CEO handles many topics and needs timely information to make sound decisions. Version B is more narrative and polished, but less efficient for that purpose.

**Learner review note — row 14:** Keep the original candidate and its bad label. The learner identified redundancy: the summary is factually correct but unnecessarily repetitive for a busy CEO. Preserve it as a verbosity failure example.

**Dataset acceptance:** The learner accepted the recommendation to keep all 20 labels as a batch based on AI-assisted assessment. Row 14 was specifically discussed and retained as bad for redundancy. No claim is made that the learner reviewed each remaining row individually.

**Judge status:** Optional Claude judge scoring has not been run. The provisional score of 1 for Version A is not a cross-family judge result.

**Module 1 evidence:** Two prompt versions, their captured outputs, the starter dataset, the learner's quality criteria, and the learner's winner selection are recorded. This exercise does not establish Ascend IQ's release readiness.
