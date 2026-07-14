# Section 44: The Asymptotic Curve of AI Quality

**Book location:** Chapter 6, Building Evals That Matter  
**Use when:** rubric, asymptotic curve, retrieval, asymptotic curve quality  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI quality usually improves quickly at first, then gets harder, slower, and never reaches
perfection.

## Actions

- Define runnable checks that exercise rubric, asymptotic curve, and retrieval.
- Set acceptable outcomes and blocker failures for rubric, asymptotic curve, and retrieval before running the evaluation.
- Run representative cases for rubric, asymptotic curve, and retrieval and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for rubric, asymptotic curve, retrieval, asymptotic curve quality needed to reproduce work on The Asymptotic Curve of AI Quality.
- Report results for rubric, asymptotic curve, retrieval, asymptotic curve quality by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

The asymptotic curve is a fancy name for a familiar pattern: early improvements are often easy, later improvements get harder, and perfection keeps moving away.

The math matters because teams can mistake a flattening curve for laziness or a tiny noisy bump for a breakthrough. The gentle interpretation is: look at the trend with uncertainty, then decide whether the next point of quality is worth the cost.

## Overview

Most AI systems improve in a familiar shape. Early changes produce obvious wins: better prompts, cleaner retrieval, stronger rubrics, fewer broken tool calls, better data, and simple safety filters. The quality curve rises quickly.

Then the curve bends. The remaining failures are rarer, more ambiguous, more domain-specific, more adversarial, more expensive to label, or more tightly tied to product tradeoffs. Each additional point of quality costs more evidence, more engineering, more policy work, or more human review.


The curve often approaches an asymptote. It may get close to the best reachable quality for the current architecture, data, model, workflow, and cost envelope. It does not become perfect. That matters because teams should stop promising perfect AI and start deciding what level of measured risk is acceptable for the use case.


## From the Field: Catching Up to the Curve

When we were working on Bing, the early relevance gains were exciting. The curve looked almost linear for a while, and it was easy to imagine catching Google soon. Some improvements were obvious from the outside: better spell correction, better synonyms, better handling of common navigational queries. Those changes produced real jumps in relevance because Google had already found many of those wins and Bing was still climbing the early part of the curve.

The harder truth was that both engines were on asymptotic curves. Google had started earlier and was spending enormous R&D, engineering talent, and compute to eke out smaller gains because the easy fixes were already gone. As Bing improved, we ran into the same shape. Each extra point required more experiments, more measurements, more slice analysis, and more care because fixing one class of queries could quietly break two others.

That was a useful lesson. Do not let early progress trick you into extrapolating a straight line. AI quality often improves fast at first, then bends. If you extrapolate, extrapolate with an asymptotic curve. One of the satisfying parts of that work was that, with enough quality measurements over time, even a regular engineer could plot the progress of two engines and estimate when they would become hard to distinguish on relevance. Let us just say the curve was not a bad guide.

## Expert Notes

Plot quality over time with uncertainty bands, not just point estimates. Look for diminishing returns, plateaus, slice-specific ceilings, and architecture-limited performance. The asymptote is not an excuse to stop testing. It is evidence that the next improvement may require a different model, data source, workflow, containment layer, or product boundary.
