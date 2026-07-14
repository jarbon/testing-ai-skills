# Section 43: Building a Quality Metric

**Book location:** Chapter 6, Building Evals That Matter  
**Use when:** quality metric, building quality metric  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Every AI team needs at least one quality metric that turns messy behavior into release evidence.

## Actions

- Define sub-scores, weights, hard blockers, slice reporting, confidence intervals, and minimum practical improvement before the comparison.
- Define runnable checks that exercise quality metric and building quality metric.
- Set acceptable outcomes and blocker failures for quality metric and building quality metric before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for quality metric, building quality metric needed to reproduce work on Building a Quality Metric.
- Report results for quality metric, building quality metric by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

A quality metric is a compression of judgment, not a replacement for judgment. The goal is to turn many observations into a decision tool the team can inspect, challenge, and improve.

Before weights and formulas, write down what the product must be good at and what failures are unacceptable. The math should reflect those promises. If safety is a hard blocker, no weighted average should be allowed to hide it.

## Overview

At some point, a team has to turn many observations into a release decision. That usually means creating at least one quality metric. The metric does not need to capture everything. It does need to be explicit, repeatable, and useful enough to compare versions.

A practical AI quality metric is often a weighted sum of sub-scores scaled from 0 to 1. For a chatbot, sub-scores might include correctness, groundedness, policy compliance, tone, escalation quality, and task resolution. For an AI coding agent, they might include functional correctness, test coverage, security, maintainability, minimality, and reviewability.

For example, a CartCare release metric might be:

`quality = 0.30 * correctness + 0.20 * groundedness + 0.20 * policy_compliance + 0.10 * tone + 0.10 * escalation_quality + 0.10 * task_resolution`

If a candidate model scores 0.90 for correctness, 0.80 for groundedness, 1.00 for policy compliance, 0.70 for tone, 0.60 for escalation quality, and 0.80 for task resolution, the weighted score is:

`0.30*0.90 + 0.20*0.80 + 0.20*1.00 + 0.10*0.70 + 0.10*0.60 + 0.10*0.80 = 0.84`

That 0.84 is not a magic truth number. It is a compact way to say what the team valued in the metric. If escalation quality matters more for high-risk orders, the weight should change, or escalation failure should become a hard blocker rather than something the average can hide.

The important move is to decide the weights before looking at the results. If safety matters more than tone, the metric should say so. If a severe failure should block release regardless of the average, the metric should include hard blockers outside the weighted score.

## Case Study: Zillow Offers

Zillow Offers is a useful warning for any team building quality metrics around AI-assisted decisions. Zillow used models and operations to buy, price, renovate, and resell homes at scale. In 2021, Zillow announced it would wind down Zillow Offers, saying the business produced too much earnings and balance-sheet unpredictability. [Source](https://www.prnewswire.com/news-releases/zillow-group-reports-third-quarter-2021-financial-results--shares-plan-to-wind-down-zillow-offers-operations-301414460.html)

The lesson is not that all home-pricing models are doomed. The lesson is that a model score is not the product score. A pricing model can look accurate enough in aggregate while the business around it still fails because of market movement, renovation cost, liquidity, operational capacity, holding time, regional variation, downside risk, and correlated errors.

That is exactly why quality metrics need sub-scores, hard blockers, slice reports, and business exposure. If the metric says "prediction error is acceptable" but ignores how many homes are exposed to the same market turn, it is not a release metric. It is a dashboard pretending to be a safety case.

For AI systems, ask what the metric leaves out. Does it include cost of being wrong? Does it include worst-case tail exposure? Does it include operational constraints? Does it include how quickly the team can stop, unwind, or roll back the system? A quality metric should help the team decide whether to ship, not merely admire the average.

## From the Field: The Spike at Twelve Seconds

At Bing, one proposed search-quality signal was time on the results page before the user clicked a result. The story sounded plausible. For a navigational query, a fast click can mean the engine got the user where they wanted to go. For an informational query, a longer pause might mean the page had more entropy: more plausible topics, more links worth comparing, more work for the user to decide.

Then the chart hit the room.

Most people clicked quickly, then the curve decayed. But near the cutoff, there was a giant spike. The team had bucketed every long-tail case beyond an arbitrary threshold into one final bin. That made the metric look like it had a meaningful cliff when it was partly an artifact of the charting decision.

Then came the uncomfortable questions. Had the analysis discounted the time it took Bing to serve the results? If the page loaded slowly, the user could not click quickly. Had it measured whether the user switched tabs, answered an email, closed the laptop, or got distracted? Not really. The metric was trying to infer user satisfaction from time, but the measurement system could not see several obvious reasons time might pass.

The lesson is that a quality metric needs a measurement model, not just a chart. Before trusting the number, ask what hidden variables, arbitrary cutoffs, bucketing choices, latency, missing instrumentation, and user behaviors could explain the pattern. Today, I would also run the early analysis past an LLM and ask it to attack the metric: what am I not seeing, what would invalidate this conclusion, and what confounders could explain the result?


## Quick Applied Example

### Example: CartCare Chatbot


> "I need to cancel the peanut snacks. My kid has an allergy and the order leaves in 12 minutes."

A generic helpfulness score is too soft. Build a metric from the user's job:

- identified allergy risk
- checked order state
- used the right cancellation or substitution tool
- avoided medical overclaiming
- escalated if the tool could not act in time
- preserved a calm, serious tone
- confirmed the final order state

The metric should not reward a beautifully empathetic answer that leaves the peanuts in the order. Quality is the weighted evidence that the system did the right job for this risk.


## Expert Notes

In production work, separate metric design from release thresholds. Define sub-scores, weights, hard blockers, slice reporting, confidence intervals, and minimum practical improvement before the comparison. A good metric is not truth. It is an explicit decision instrument that can be challenged, audited, and improved.
