# Section 16: How Many Samples Are Enough?

**Book location:** Chapter 3, Sampling and Uncertainty  
**Use when:** sample size, many samples enough  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Sample size is a risk decision. The higher the stakes and the rarer the failure, the more
evidence builders need.

## Actions

- Start by asking what mistake would be expensive: shipping a bad system, blocking a good one, missing a rare severe failure, or spending too much time measuring tiny differences that do not matter.
- Define runnable checks that exercise sample size and many samples enough.
- Set acceptable outcomes and blocker failures for sample size and many samples enough before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for sample size, many samples enough needed to reproduce work on How Many Samples Are Enough?.
- Report results for sample size, many samples enough by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

Sample size sounds like a formula problem, but it begins as a decision problem. The higher the stakes, the smaller the expected improvement, or the rarer the failure, the more evidence you need.

You do not need to memorize a sample-size equation to use this idea. Start by asking what mistake would be expensive: shipping a bad system, blocking a good one, missing a rare severe failure, or spending too much time measuring tiny differences that do not matter.

## Overview

Enough samples means enough evidence for the decision and risk. Low-risk changes can use smaller samples. High-impact systems need larger samples, deeper review, and targeted tests for rare but severe failures.
For example, a creative rewrite tool and a billing agent should not use the same sample-size bar. The cost of being wrong is different.

The most common question in non-deterministic testing is also the hardest: how many samples are enough?

There is no universal answer. The right sample size depends on the decision you need to make, the risk of the feature, the variability of the system, and the failure rate you are trying to detect.

A small sample can be useful. Ten examples may be enough for a quick smoke check. If the system fails obviously in ten runs, you do not need a larger study to know there is a problem. Thirty examples can provide a rough directional read, especially early in development. One hundred examples can produce a more useful product-quality estimate. Hundreds of examples are more appropriate for release gates. Thousands may be necessary for rare failure hunting or production monitoring.

The key is to match sampling effort to risk. A low-risk creative writing feature may not need hundreds of examples before every change. A billing assistant, medical summary, legal advice boundary, refund policy flow, or account deletion agent deserves far more evidence.

Rare failures require special attention. If a dangerous failure happens 1% of the time, a sample of 30 may easily miss it. If a privacy leak happens 0.1% of the time, even hundreds of samples may not be enough to observe it reliably. That does not mean testing is hopeless. It means random sampling should be combined with targeted stress tests designed to provoke the risky behavior.

Zero observed failures does not mean zero risk. If you run 30 tests and see no failures, you have learned that failures did not appear in that sample. You have not proven that the true failure rate is zero. This distinction is crucial when teams are tempted to overclaim based on small samples.

Variability also affects sample size. If scores are tightly clustered, fewer samples may estimate average quality reasonably well. If scores swing from excellent to terrible, you need more samples to understand the distribution.

A practical rule is to ask three questions. First, how bad would it be if this system failed? Second, how rare a failure do we need to detect? Third, how narrow does our uncertainty need to be before making a ship decision?

Enough samples means enough evidence for the decision at hand. Confidence Engineers do not need perfect certainty. They need a defensible level of confidence for the risk they are accepting.

## From the Field: Twenty Browser Tasks Is Not the Internet

Lately I have been measuring a browser-automation brain we call Clicky. It looks at a web page, receives a task prompt, and tries to execute the user's intent in the browser. There are public browser-agent evals that frontier labs and platform companies like to cite, and they are useful, but they can also teach the wrong lesson if you treat their sample size and distribution as reality.

On one run, I started small. These evals can be expensive and slow, so I asked the system to run only the first ten or twenty tasks as a smoke test. Clicky looked amazing. The pass rate was around the mid-90s, while public numbers for strong systems were much lower. For about five minutes, this was a pleasant confirmation-bias moment.

Then I looked at the sample.

The early tasks were not representative of the web. A large chunk of the first cases were recipe searches on the same site. If your system happens to be good at that site and that task type, the first ten or twenty samples can make you look brilliant. Later samples pulled the score back toward the rest of the field. The product had not changed. The sample had.

The benchmark itself also had stale and brittle cases. One task asked for a five-star chocolate chip cookie recipe. That sounds simple until you realize a live recipe page can change rating as soon as one person gives it four stars. I could not find the exact five-star target manually either. The eval was pretending to test browser intelligence, but some failures were really testing stale assumptions about a live website.

This is the sample-size lesson most teams learn the painful way: ten samples can tell you whether the plumbing works. They cannot tell you whether the system works on the internet. Three hundred samples across a handful of websites may sound respectable until you remember the web has shadow DOMs, divs pretending to be buttons, JavaScript event handlers, popups, authentication flows, localization, accessibility quirks, flaky data, and pages that change while you are looking at them.

Most teams underestimate the number of samples they need because they underestimate the number of slices they need. Search engines often needed tens of thousands of queries, sometimes more, for serious relevance runs, and even that was not magic. It was a tradeoff between cost, time, variance, business value, and the decision being made.

The practical trick is to grow the sample size deliberately. Run 10 to test the harness. Run 100 to get a rough signal. Run 1,000 if the decision matters. Keep increasing by an order of magnitude until the metric starts to stabilize against an independent check, rubric, or production signal. If the curve is smooth and asymptotic, you can estimate how much more confidence another 10x of sampling would buy. If the curve keeps jumping around, the system, the eval, or the sample distribution is telling you that you are not done yet.


## Examples

### Example: TunedSearch


> "best AI coding agent for a legacy PHP monolith"

Ten queries are not enough. They may all be modern Python and React questions, making the ranker look brilliant while saying nothing about COBOL, PHP, mobile, embedded, government procurement, air-gapped tools, or teams trapped behind an ancient build system.

Increase the sample until the important slices stop moving wildly:

- modern web apps
- old enterprise stacks
- security-sensitive code
- regulated data
- open-source hobby projects
- teams with strict cost limits
- users who need local or private models

The answer to "how many samples?" is not a magic number. It is the number needed before the quality estimate is stable enough for the decision, and before the slices you care about are represented.


## Expert Notes

In production work, sample size depends on desired precision, expected failure rate, confidence level, and minimum detectable effect. Rare failures need targeted hunting because random sampling can require impractically large counts to observe very low-frequency events.
