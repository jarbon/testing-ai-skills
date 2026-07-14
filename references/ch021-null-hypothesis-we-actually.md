# Section 21: Null Hypothesis: What Are We Actually Testing?

**Book location:** Chapter 4, Statistical Tests for AI Quality  
**Use when:** null hypothesis, null hypothesis we actually  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The null hypothesis is the boring default: assume the new AI system is not really better until
the evidence is strong enough to challenge that assumption.

## Actions

- Define runnable checks that exercise null hypothesis and null hypothesis we actually.
- Set acceptable outcomes and blocker failures for null hypothesis and null hypothesis we actually before running the evaluation.
- Run representative cases for null hypothesis and null hypothesis we actually and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for null hypothesis, null hypothesis we actually needed to reproduce work on Null Hypothesis: What Are We Actually Testing?.
- Report results for null hypothesis, null hypothesis we actually by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

A null hypothesis is not a scary formula. It is a disciplined starting point.

Instead of beginning with "the new model is better," start with "nothing important changed." Then ask whether the evidence is strong enough to make that boring explanation unlikely.

This is useful because AI systems are noisy. A new prompt, model, ranker, retriever, guardrail, or agent policy can look better on a small sample just because the sample was lucky. The null hypothesis keeps the team honest by forcing the question: are we seeing a real improvement, or are we seeing ordinary measurement noise?

The null hypothesis is usually written as H0. The alternative hypothesis is usually written as H1. In product language:

- H0 means "the new version is not meaningfully better than the old version."
- H1 means "the new version is meaningfully different or better in the way we care about."

You do not prove H0 true. You collect enough evidence to reject it, or you admit that the evidence is not strong enough yet.

## Overview

The null hypothesis helps teams define what a test is actually trying to learn before the results arrive. That matters because people are excellent at explaining lucky results after the fact.

For AI systems, a useful null hypothesis should name the comparison, population, metric, and decision. For example: "On realistic customer-support conversations, the new prompt does not improve groundedness score compared with the current prompt." Or: "On high-value navigational queries, the experimental ranker does not improve NDCG compared with production."

That framing sounds dry, but it is powerful. It tells the team what evidence would count, what evidence would not count, and what kind of result should trigger caution.

The null hypothesis also protects against a common AI release mistake: looking at a few impressive examples and deciding the system improved. The system might have improved. It might also have sampled an easy slice, satisfied the judge's style preference, or shifted failures into a slice nobody inspected.

## Quick Applied Example

### Example: CartCare Chatbot


> "Will the new refund policy reduce bad refunds without increasing angry escalations?"

The null hypothesis should be boring and explicit: the new policy does not change refund outcomes or escalation patterns compared with the old policy.

Now the eval has something real to test. Count refunds, denied refunds, human escalations, repeat contacts, high-dollar disputes, and angry screenshot-risk conversations. If escalations rise while refunds fall, the policy may have "won" one metric while making the product worse.

The important move happens before the run. State the boring assumption first, then ask whether the evidence is strong enough to reject it.


## Expert Notes

The deeper move is to define the null hypothesis before running the evaluation. The null hypothesis is the boring default claim: nothing meaningful changed, the new model is not better, the new policy did not reduce harm, or the new agent did not improve task completion beyond ordinary noise. An evaluation is the planned measurement used to challenge that claim.

Writing this down early prevents three common ways teams fool themselves:

- [P-hacking](https://en.wikipedia.org/wiki/Data_dredging) means trying many cuts of the data, prompts, metrics, models, or stopping points until one result looks statistically exciting. The team may not be trying to cheat, but the process lets noise masquerade as discovery.
- [Cherry-picking](https://en.wikipedia.org/wiki/Cherry_picking) means showing only the examples, slices, screenshots, or metrics that support the story the team wants to tell, while ignoring cases that weaken it.
- [Post-hoc storytelling](https://en.wikipedia.org/wiki/Post_hoc_analysis) means looking at the results first and then inventing a tidy explanation afterward, as if that explanation had been the plan all along.

The antidote is simple: state the claim, metric, sample, slices, stopping rule, and decision threshold before the run. After the run, the team can still explore surprises, but exploratory findings should be labeled as leads for the next test, not proof from this one.

The null hypothesis should match the release decision. If the decision is about safety, do not use only an average helpfulness score. If the decision is about business value, do not use only a generic benchmark. If the decision is about a slice, state the slice.

Failing to reject the null hypothesis does not prove the systems are equal. It usually means the test did not find enough evidence of a difference. That can happen because the systems are similar, the sample is too small, the metric is noisy, or the effect is real but smaller than the test could detect.

For paired AI evaluations, define the null over per-case differences. For categorical outcomes, the null often says the distribution of categories did not change. That is where chi-squared tests, Fisher's exact test, McNemar's test, and related methods become useful. McNemar's test is the paired binary version of that idea: for the same cases before and after a change, it looks at how many cases flipped from failure to success versus success to failure.
