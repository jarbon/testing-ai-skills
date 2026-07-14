# Section 1: The Next Generation AI Builder Will Measure Uncertainty

**Book location:** Chapter 1, The End of One-Run Testing  
**Use when:** behavior distributions, repeated runs, sampling, uncertainty, release confidence  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Modern quality work is moving from checking single outputs to measuring behavior at scale, over
time, and through sampling. Developers who can explain uncertainty will shape how AI systems
ship.

## Actions

- Define runnable checks that exercise behavior distributions, repeated runs, and sampling.
- Set acceptable outcomes and blocker failures for behavior distributions, repeated runs, and sampling before running the evaluation.
- Run representative cases for behavior distributions, repeated runs, and sampling and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for behavior distributions, repeated runs, sampling, uncertainty needed to reproduce work on The Next Generation AI Builder Will Measure Uncertainty.
- Report results for behavior distributions, repeated runs, sampling, uncertainty by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Think of this book as a shift from checking one answer to measuring a behavior pattern. A chatbot, recommendation engine, summarizer, fraud model, or agent can look good in one demo and still fail too often across real traffic. The work is to measure that behavior across enough examples to make a responsible decision.
For example, one refund answer may be perfect, but the next hundred answers may reveal policy confusion, uneven tone, and a few dangerous promises. The next-generation AI builder sees the distribution, not just the demo.

Testing used to be simpler. You gave software an input, checked the output, and decided whether the result matched your expectation. That model still matters. A login form should still reject a bad password. A calculator should still return the same sum. A checkout flow should still charge the correct amount.

But that is no longer the whole testing world.

Modern products increasingly include systems that do not behave the same way twice. LLMs may answer the same question twice, in different words, with the same meaning and impact. Recommendation engines may change ranking order. ML models may drift after retraining. AI agents may use different paths and tools to complete the same task. Distributed services may process events in different orders depending on timing.

All of those systems can also exhibit varying degrees of correctness and failure. An answer can be mostly right but dangerously incomplete. A search result page can satisfy one user intent while missing another. A coding-agent patch can pass tests while adding maintainability risk. That is why the work is not only catching broken outputs; it is measuring behavior well enough to understand what needs to be improved and calibrate the product, rubric, judge, sample, or release gate.

Testing is the doorway into this work because it is the word software teams already know. But the destination is broader: confidence engineering. The job is to build enough evidence about behavior, safety, cost, reliability, user value, observability, and reversibility that a team can make a responsible decision about release.

For developers building AI features, this changes the center of gravity. The question is no longer only, "Did the system return the expected answer?" The better question is, "Across a realistic sample of cases, how often does this system behave acceptably, how bad are the failures, and how confident are we in that estimate?"

That sounds mathematical, but it does not require becoming a statistician. It requires a practical testing mindset. You need to test at scale because individual examples can mislead you. You need to understand sampling because one run tells you almost nothing. You need to understand variance because not every difference is a bug. You need to understand confidence intervals because sample results are estimates, not exact truth. You need to understand p-values and t-tests well enough to compare versions without fooling yourself.

LLMs can help with this work. They can judge outputs against rubrics, summarize failures, cluster similar issues, compare two responses, and even help explain statistical results. But the accountable builder still owns the judgment. The builder defines the rubric. The builder chooses the sample. The builder watches for rare failures. The builder decides whether the evidence is strong enough to ship. And yes, more often the builder is also the AI, which also needs these skills. When that happens, there still needs to be a responsible human or accountable team deciding what the AI is allowed to build, evaluate, recommend, and release.

A next-generation AI builder does not say, "I tried it once and it worked." They can say something more useful: "We tested 300 realistic cases. The average quality score improved from 7.6 to 8.2. The 95% confidence interval for the improvement is +0.3 to +0.9. Policy failure rate dropped from 6% to 2%. No critical safety failures were observed. The metric definitions and calculation methods are documented for stakeholders. Recommendation: canary, monitor the risky slices, and promote only if production telemetry stays inside the release thresholds."

That is a different level of quality conversation. It gives product leaders, engineers, and compliance teams evidence they can reason about. It also gives developers a more strategic way to own AI behavior instead of tossing uncertainty over the wall.

This book is about that shift. It starts with testing because that is the familiar entry point, then connects the pieces that actually support a production decision: rubrics, scoring, sampling, confidence intervals, t-tests, p-values, metamorphic testing, stratified reporting, rare failure hunting, release gates, monitoring, incident response, governance, and product judgment.

This discipline should make judgment clearer, not testing colder or more mechanical. When systems are unpredictable, quality comes from measuring uncertainty honestly and deciding what level of risk is acceptable.

## Should This Be an AI System?

Before measuring an AI system, ask whether the product should be an AI system at all. The first confidence-engineering decision is not model choice. It is use-case choice.

Some problems need flexible language, fuzzy judgment, personalization, summarization, retrieval, perception, or open-ended assistance. AI may be the right tool there. Other problems need exactness, repeatability, auditability, low latency, or clear legal accountability. A deterministic form, rules engine, search filter, database query, or workflow may be cheaper, safer, and easier to prove correct.

A useful use-case review asks:

- What user problem needs AI rather than ordinary software?
- What happens when the answer is wrong, late, biased, stale, expensive, or impossible to explain?
- What evidence would convince us the system is better than the non-AI baseline?
- Which parts must be deterministic even if the model output varies?
- Can the system fail safely, refuse, escalate, or roll back?
- Can we afford the latency, token cost, monitoring, incident response, and human review the feature will require?

This is not anti-AI. It is pro-product. The fastest way to ship a trustworthy AI product is often to make the AI surface smaller, surround it with deterministic contracts, and measure only the uncertainty that creates real user value.

## Expert Notes

The main move is separating observation from inference. The sample result is what you saw. The confidence interval is what you estimate about the wider population. The release decision is a risk judgment that uses both, plus business context, severity, reversibility, and monitoring plans.
