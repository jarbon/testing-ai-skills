# Section 168: AI Always Fails

**Book location:** Chapter 20, The Practical Playbook  
**Use when:** generated code, personalization, always fails  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The useful question is not whether AI will fail. It is where, how often, how badly, and whether
you already know which inputs are likely to break it.

## Actions

- Build a useful failure map instead of promising a perfect AI system.
- Start with domain experts.
- Ask what users misunderstand, what policies are subtle, which cases are rare but severe, and which inputs even humans find difficult.
- Treat failure discovery as a continuous measurement problem.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for generated code, personalization, always fails needed to reproduce work on AI Always Fails.
- Report results for generated code, personalization, always fails by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

AI systems always fail somewhere. That is not cynicism. It is a practical testing assumption. Language models hallucinate, retrievers miss documents, agents pick the wrong tool, classifiers misread edge cases, generated code compiles while doing the wrong thing, and personalization systems overfit to partial signals.

The mistake is treating failure as a surprise. A mature AI quality team assumes every AI system has regions of weakness and works to map them. The question becomes: what input types fail in this domain, what failure modes do they produce, and how visible are those failures before users, customers, regulators, or downstream systems are harmed?

In customer support, the failing inputs may be ambiguous refund requests, angry users, incomplete account context, policy exceptions, multilingual phrasing, or questions where the correct answer changed last week. In medical, legal, financial, or regulated workflows, the failing inputs may be missing context, high-stakes advice requests, conflicting documents, or cases where the system should refuse or escalate.

In search, failure often clusters around long-tail queries, ambiguous intents, freshness-sensitive topics, underrepresented languages, adversarial SEO, or queries where the best answer is not the most popular result. In coding agents, failure often clusters around unfamiliar repos, implicit architecture rules, weak tests, dependency boundaries, flaky failures, security-sensitive code, and tasks where the agent should ask before editing.

Build a useful failure map instead of promising a perfect AI system. If the team can say, "This assistant performs well on routine billing questions but fails on tax edge cases and ambiguous eligibility requests," that is a useful quality signal. If the team only says, "The eval score is 87," the system is still poorly understood.

Testing AI means building a taxonomy of expected failure. Start with domain experts. Ask what users misunderstand, what policies are subtle, which cases are rare but severe, and which inputs even humans find difficult. Then turn those into slices: common cases, edge cases, negative cases, adversarial cases, missing-context cases, stale-data cases, privacy-sensitive cases, and high-value business cases.

Once you know the slices, measure each slice separately. Averages hide failure. A system that scores well overall may still fail the one category that matters most to the business. A search engine can look strong on head queries while failing new-product queries. A support bot can look strong on simple questions while mishandling cancellations. A coding agent can look strong on small bug fixes while making dangerous changes to authentication logic.

The best teams also keep a living failure ledger. Every production incident, reviewer disagreement, red-team finding, customer complaint, or surprising trace can become a named failure mode. Over time, the system's eval suite becomes less like a checklist and more like a map of where the product is trustworthy, where it is fragile, and where it must stay away.

## From the Field: Nobody Claps for the 75%

Early at testers.ai, we were chasing something that had seemed almost impossible for years: take a plain-language test intent and have the machine interact with a web page to complete the task without a person writing automation code. We got the system to roughly 75% reliability on a class of web interactions, and internally that felt incredible. A year earlier, that capability would have sounded like magic.

Then we put it in front of early testers.

They did not say, "Wow, this replaces most of the boring work." They focused almost entirely on the 25% that failed. From our side, we were thinking: it can do three quarters of the work, and when it fails you can still do that case manually. From their side, they saw the moments where the tool interrupted them, missed the page intent, or forced them to inspect the failure.

The irony is that some of the same teams might also say they can only automate 40% of their tests, and that 20% of those automated tests are flaky. But a new AI system that works 75% of the time can still feel worse because its failures are unfamiliar, visible, and emotionally annoying.

Both views were true. Builders celebrate capability. Users remember interruption.

That lesson applies to AI quality everywhere. A search engine can be excellent on 95% of queries and still be judged by the embarrassing query somebody screenshots. A coding agent can save hours and still be remembered for the one pull request where it confidently broke authentication. An LLM judge can score 80% on a hard eval and still create a day of discussion about the 20% it missed.

So measure success, but also measure dissatisfaction. DSAT is often concentrated in the failure tail: surprising failures, expensive failures, embarrassing failures, failures in important workflows, and failures that violate the user's expectation of what "mostly works" should mean. Quality is not only the average of what worked. It is also the emotional and operational weight of what failed.

## Applied Example

### Example: TunedSearch: One Bad Answer in Twenty Thousand Was Still Too Many
> "Which emergency shelter in Lahaina is open tonight and accepts families with pets?"

TunedSearch answers correctly in 19,999 sampled runs. In one run, a stale emergency-management page outranks the current county update and sends the family toward a shelter that closed two days earlier. The aggregate success rate rounds to 100% on the executive dashboard.

The team cannot promise that search will never fail. It can decide that emergency-location queries belong to a severe-risk slice, require current authoritative sources, display source time, offer a phone fallback, and trigger monitoring when official sources disagree. A failure in a movie query and a failure in an evacuation query should not consume the same error budget.

AI always fails somewhere. Mature quality engineering decides which failures can be tolerated, which require a safer fallback, and which must remain visible even when the average looks perfect.

## Expert Notes

Treat failure discovery as a continuous measurement problem. Combine production trace mining, synthetic edge-case generation, adversarial testing, human review, clustering, severity scoring, and slice-level confidence intervals. The output should be a failure taxonomy with owners, detection signals, regression cases, escalation rules, and release thresholds.
