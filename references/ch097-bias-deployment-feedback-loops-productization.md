# Section 97: Bias in Deployment, Feedback Loops, and Productization

**Book location:** Chapter 12, Data, Bias, Raters, and Incentives  
**Use when:** bias deployment feedback loops productization  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Even a well-tested model can become biased when the product around it changes who is seen,
measured, and rewarded.

## Actions

- Track satisfaction, reformulations, long-click quality, source credibility, and whether certain slices are pushed toward lower-quality information because they clicked it once.
- Define runnable checks that exercise bias deployment feedback loops productization.
- Set acceptable outcomes and blocker failures for bias deployment feedback loops productization before running the evaluation.

## Evidence to Produce

- Track satisfaction, reformulations, long-click quality, source credibility, and whether certain slices are pushed toward lower-quality information because they clicked it once.
- Preserve the inputs, versions, configurations, raw outcomes, and results for bias deployment feedback loops productization needed to reproduce work on Bias in Deployment, Feedback Loops, and Productization.
- Report results for bias deployment feedback loops productization by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Deployment changes the system. A model that performed acceptably in offline evals may behave differently when exposed to real users, market incentives, content creators, attackers, and feedback loops.

Feedback loops are especially important. If a system promotes certain content, that content gets more clicks. If clicks become training data, the system learns that promoted content is preferred. Over time, the model can amplify early advantages, suppress minority content, or mistake exposure for quality.

Productization bias appears when business goals, UI choices, latency limits, monetization, moderation policy, and logging decisions shape what quality means.

## Case Study: Microsoft Tay

Microsoft's Tay chatbot is one of the cleanest public examples of an AI system changing once it met the world. Tay was released on Twitter in 2016 as a conversational experiment. Very quickly, people learned how to push it toward offensive and abusive outputs, and Microsoft took it offline. Microsoft's own account described the coordinated attacks and the product changes the company believed were necessary before trying again. [Source](https://blogs.microsoft.com/blog/2016/03/25/learning-tays-introduction/)

The AI quality lesson is not simply "people on the internet are terrible," though that is not a bad starting assumption. The deeper lesson is that deployment is part of the model environment. A chatbot trained, filtered, and evaluated in a lab can become a different product when exposed to coordinated abuse, copycat behavior, social incentives, screenshots, and public feedback loops.

The failure was not only about a bad answer, It was about how quickly users, platform dynamics, and public incentives shaped the system's behavior and brand risk. Test the model, yes. But also test the launch environment, abuse loops, moderation latency, replay attacks, screenshot risk, escalation rules, and the product team's ability to shut down or degrade safely.

## High-Stakes Examples

### Example: TunedSearch


> Users click sensational AI layoffs articles more than sober labor-market analysis.

If the system learns only from clicks, it may promote scarier headlines, which get more clicks, which teach the system to promote even more of them. The product can drift from relevance into attention harvesting.

The eval should separate engagement from user value. Track satisfaction, reformulations, long-click quality, source credibility, and whether certain slices are pushed toward lower-quality information because they clicked it once.


## Expert Notes

In a real release review, bias testing after launch should include exposure metrics, feedback-loop audits, slice dashboards, drift detection, intervention tests, and governance for when business metrics conflict with fairness or safety metrics.
