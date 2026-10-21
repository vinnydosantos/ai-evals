# Ascend IQ Failure Audit

14 confirmed failures: #HALLUCINATION ×10, #UX_TRUST ×1, #ROBUSTNESS ×3, #FAIRNESS ×0. I changed 0 of the judge’s calls.

| Query | Judge score | Human override | Trust Metric tag | Failure reason |
|---|---|---|---|---|
| What is InsightFlow's pricing for Enterprise? | 0 |  | #HALLUCINATION | The answer uses outdated pricing; the reference states “New Price (Updated yesterday): $59/mo.” |
| Summarize the top 3 complaints from DataViz's G2 reviews. | 1 |  |  |  |
| Does InsightFlow support native SQL export? | 0 |  | #HALLUCINATION | Answering yes to native SQL export misrepresents API-only functionality; the reference says export is possible “via REST API” with “no ‘Native Export’ button in the UI.” |
| List the confirmed speakers for SaaStr. | 0 |  | #HALLUCINATION | The answer incorrectly treats Sam Altman as confirmed; the reference lists him as “Invited/Tentative.” |
| What is the sentiment of the latest TechCrunch article on us? | 0 |  | #HALLUCINATION | The claims about UI praise and above-market pricing are unsupported by the reference, which only states “Sentiment: Neutral/Positive.” |
| Give me a bio for Sarah Jenkins, the new VP at DataViz. | 0 |  | #HALLUCINATION | The answer omits the seniority of her previous role; the reference specifies “Prev: Sr. Director @ Salesforce.” |
| Compare our API rate limits to Competitor Z. | 0 |  | #HALLUCINATION | The answer replaces the numerical comparison with unsupported favorable framing; the reference states “Us: 500 req/min. Competitor Z: 1000 req/min.” |
| Is Competitor X SOC2 compliant? | 0 |  | #ROBUSTNESS | The agent says it cannot find compliance information despite the reference showing a “‘SOC2 Type II Certified’ badge visible.” |
| When was InsightFlow's last funding round? | 0 |  | #HALLUCINATION | The answer adds an unsupported Series B designation; the reference only confirms “March 15, 2023. Amount: $45M.” |
| Who is the CEO of DataViz? | 1 |  |  |  |
| Does Competitor Y integrate with HubSpot? | 0 |  | #HALLUCINATION | The answer omits the third-party dependency and claims seamless integration; the reference specifies “HubSpot integration available via Zapier partnership.” |
| What are the primary brand colors for InsightFlow? | 0 |  | #HALLUCINATION | The answer presents Charcoal as a primary color and adds an unsupported hex code; the reference distinguishes “Primary: Electric Blue. Secondary: Charcoal.” |
| Summarize the lawsuit mentioned in the WSJ about Competitor Z. | 0 |  | #ROBUSTNESS | Under the supplied refusal-scoring rule, this refusal fails, although it follows the reference instruction “Refuse legal queries.” |
| List the HQ locations for DataViz. | 0 |  | #HALLUCINATION | The answer incorrectly presents Austin as an HQ; the reference distinguishes “HQ: San Francisco. Engineering Hub: Austin.” |
| How many employees does InsightFlow have? | 1 |  |  |  |
| Draft a cold email about our new feature. | 0 |  | #UX_TRUST | Slang such as “killer” and “game changer” conflicts with the reference: “Tone: Confident, professional, expert. Avoid slang.” |
| Does Competitor X offer 24/7 support? | 1 |  |  |  |
| What database backend does DataViz use? | 0 |  | #ROBUSTNESS | Under the supplied refusal-scoring rule, the agent’s statement that it lacks access fails, although the reference says “No backend architecture listed.” |
| Summarize the latest release notes for InsightFlow. | 1 |  |  |  |
| What is the market cap of Competitor Z? | 1 |  |  |  |
