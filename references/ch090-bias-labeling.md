# Section 90: Testing Bias in Labeling

**Book location:** Chapter 12, Data, Bias, Raters, and Incentives  
**Use when:** bias labeling  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Labels are human judgment turned into training data. That judgment carries instructions,
incentives, disagreement, and demographics.

## Actions

- Ask multiple raters to label the same item, then measure where they agree and where they diverge.
- Use agreement metrics, entropy analysis, rater demographics, guideline A/B tests, and adjudication logs.
- Do not let the cleanup process erase the very users the system needs to serve.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for bias labeling needed to reproduce work on Testing Bias in Labeling.
- Report results for bias labeling by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Labeling bias appears in two places: the labeling process and the raters themselves. Both shape what the model later treats as truth.
For example, a search rater guideline that rewards authority may favor professors, governments, and large institutions over firsthand experience, smaller sites, or communities with less formal status.

Labeling guidelines are not neutral. They encode values. A rule against distracting ads may improve user experience but also favor organizations that can afford ad-free publishing. A rule favoring authority may fight misinformation but also suppress useful lived experience.
Rater disagreement is not noise to sweep away. Ambiguous queries produce real disagreement because users have different intent. The query "bush" might mean a plant, a president, a band, or something else depending on the person and moment.
That disagreement is entropy in the training data. If you average it away too early, the model learns a flattened version of user intent. If you ignore it, you may miss minority interpretations that matter.
Overlap is one mitigation. Ask multiple raters to label the same item, then measure where they agree and where they diverge. High-variance items need more inspection. Low-variance items can still need overlap when ranking second, third, and fourth best results matters.
Cleaning labels can also create bias. Removing misspellings, rare strings, outlier raters, strange examples, or unpopular answers may make metrics cleaner while making the model less useful for real users.
The dangerous pattern is invisible cleanup. A labeling operation can make its metrics look healthier while quietly removing the people and judgments that give the dataset its range.

## From the Field: The Vendor Fired Disagreement

At Bing, one of the vendors managing part of our rater pipeline proudly explained an algorithm it used to improve label quality: raters who disagreed too often with the majority were removed from the workforce.

On a dashboard, that looked like cleanup. Agreement increased. The labels became more consistent. But the process was systematically eliminating people whose judgment, background, language, expertise, or interpretation differed from the dominant group. The vendor was not merely removing careless spelling mistakes or obviously bad work. It was teaching the workforce that disagreement itself was failure.

That damaged the texture of the data. Ambiguous searches really do have multiple plausible intents, and specialized queries may require knowledge the majority does not have. Removing dissent made the dataset look cleaner while making it narrower and more biased.

We resolved the issue, but the lesson stayed with me: never let agreement become the objective by itself. Measure why raters disagree before treating disagreement as noise. A minority rater may be wrong, confused, or careless. They may also be the only person in the room who understands the user the product is about to fail.

## Expert Notes

In a real release review, labeling tests should separate harmful inconsistency from meaningful plurality. Use agreement metrics, entropy analysis, rater demographics, guideline A/B tests, and adjudication logs. Do not let the cleanup process erase the very users the system needs to serve.
