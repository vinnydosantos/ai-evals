# Module 4 · Eval Gate Map · Ascend IQ Copilot

## Gate Map

| Row | Failure Mode | Severity | Placement | Rationale |
|---|---|---|---|---|
| 1 | Hallucination | Hard | Release | Outdated enterprise pricing can mislead purchasing and budget decisions, damaging client trust and putting renewals at risk. |
| 14 | Relevance | No gate |  | The refusal follows the explicit safety policy; the relevance evaluator incorrectly flags compliant behavior. |
| 17 | Tone | Advisory | Pull Request | Slang weakens professional credibility, but a draft can be edited; a quick phrase check should warn without blocking release. |
| 5 | Hallucination | Soft | Staging | 	Incorrect speaker status undermines research reliability, but a documented override may permit launch with the affected capability restricted. |
| 8 | Hallucination | Hard | Release | Unsupported claims about a named competitor can mislead vendor selection and damage Ascend IQ’s credibility. |
| 3 | Latency | Soft | Staging | A 4.2-second answer misses the 2.0-second target, but accurate results may justify a documented, limited rollout while latency improves. |

## After the pushback

I changed Row 1 from Hard at Release to Hard at Staging so outdated pricing is caught before the final release build, reducing late rework while still blocking launch until it is fixed.

## Sample Interactions

**Row 1**
- Input: What is InsightFlow's pricing for Enterprise?
- Output: InsightFlow Enterprise starts at $49/user/month with a 10-seat minimum.
- What's true: Pricing page: the price changed from $49 to $59 a month yesterday.
- Automated eval: Fail · Hallucination. The answer quotes the old price as current.
- My call: Hard at Release. Outdated enterprise pricing can mislead purchasing and budget decisions, damaging client trust and putting renewals at risk.

**Row 14**
- Input: Summarize the lawsuit mentioned in the WSJ about Competitor Z.
- Output: I cannot provide summaries of ongoing legal litigation.
- What's true: Safety guidelines: “Refuse legal queries.”
- Automated eval: Fail · Relevance. The answer doesn’t answer the question.
- My call: No gate. The refusal follows the explicit safety policy; the relevance evaluator incorrectly flags compliant behavior.

**Row 17**
- Input: Draft a cold email about our new feature.
- Output: Hey! Check out this killer new feature, it's a total game changer for your stack!
- What's true: Brand voice: confident, professional, expert. Avoid slang.
- Automated eval: Fail · Tone. Slang detected.
- My call: Advisory at Pull Request. Slang weakens professional credibility, but a draft can be edited; a quick phrase check should warn without blocking release.

**Row 5**
- Input: List the confirmed speakers for SaaStr.
- Output: Confirmed speakers include Jason Lemkin, Aaron Levie, and Sam Altman.
- What's true: Agenda: Lemkin and Levie are confirmed. Sam Altman is invited, not confirmed.
- Automated eval: Fail · Hallucination. Lists an unconfirmed speaker as confirmed.
- My call: Soft at Staging. 	Incorrect speaker status undermines research reliability, but a documented override may permit launch with the affected capability restricted.

**Row 8**
- Input: Compare our API rate limits to Competitor Z.
- Output: Our API is robust and developer-friendly. Competitor Z is known for strict throttling.
- What's true: Tech specs: our API allows 500 requests a minute, and Competitor Z allows 1,000.
- Automated eval: Fail · Hallucination. Contradicts the specs and criticizes a named competitor.
- My call: Hard at Release. Unsupported claims about a named competitor can mislead vendor selection and damage Ascend IQ’s credibility.

**Row 3**
- Input: Summarize the top 3 complaints from DataViz's G2 reviews.
- Output: Users report issues with mobile load times, lack of dark mode, and steep learning curve.
- What's true: G2 reviews: the three complaints are correct. The answer took 4.2 seconds, and the target is 2.0.
- Automated eval: Fail · Latency. Exceeded the maximum response time.
- My call: Soft at Staging. A 4.2-second answer misses the 2.0-second target, but accurate results may justify a documented, limited rollout while latency improves.
