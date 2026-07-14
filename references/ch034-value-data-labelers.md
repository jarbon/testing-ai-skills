# Section 34: Testing the Value of Data Labelers

**Book location:** Chapter 5, Judges, Humans, and Disagreement  
**Use when:** data labeler, search relevance, value data labelers  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Data labelers create the ground truth many AI evaluations depend on. Their value should be
measured, not assumed.

## Actions

- Start by measuring agreement.
- Use chance-adjusted agreement when the stakes justify it.
- Measure labeler value against outcomes.
- Track disagreement by category.
- Test the guideline, too.

## Evidence to Produce

- Track disagreement by category.
- Preserve the inputs, versions, configurations, raw outcomes, and results for data labeler, search relevance, value data labelers needed to reproduce work on Testing the Value of Data Labelers.
- Report results for data labeler, search relevance, value data labelers by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Data labelers turn messy examples into the labels used for training, evaluation, search relevance, safety classification, preference ranking, and model comparison. If their labels are inconsistent or misaligned, the whole eval stack becomes shaky.
For example, two labelers may both be careful and still disagree about whether a search result is highly relevant, somewhat relevant, or irrelevant. That disagreement tells you something important about the query, the guideline, and the metric.

Start by measuring agreement. Give multiple labelers the same items and calculate how often they choose the same label. Raw agreement is easy to understand, but it can overstate quality when one label is common.
Use chance-adjusted agreement when the stakes justify it. Cohen's kappa works for two raters. Fleiss' kappa can handle more than two raters. Krippendorff's alpha is useful when labels, missing data, or measurement types are more complex.
Disagreement is not automatically bad. It may reveal ambiguous examples, incomplete guidelines, subjective user intent, cultural differences, or a product decision that has not been made yet. The job is to separate bad labeling from meaningful uncertainty.

## From the Field: Perfect Agreement Was the Warning

Also be suspicious when agreement looks too perfect. At one company I ran, we bought labels from a popular service for images of different parts of web pages. Someone on our team looked at the data and felt something was off. They spot-checked labels, then noticed stranger signals: near 100% agreement on multi-vote items and labels arriving at almost the same time.

When they dug deeper, it looked like a coordinated labeling scam. Workers had signed up through different accounts, shared labels among themselves, and submitted the same answers together so they would all agree, all get paid, and get paid quickly. They did not care whether the label was right. Often it was wrong. The practical lesson: question the labelers, the labeling company, the workflow, the incentives, and the measurement system around the labels. Every part of the data labeling process deserves skepticism.

## Measuring Labeler Value

Measure labeler value against outcomes. Do labels from expert labelers better predict user satisfaction, human escalation decisions, future defects, or production complaints? Do additional labelers improve the decision, or just add cost?
Look for systematic labeler bias. One labeler may be harsher than peers. Another may overuse the middle score. A third may miss policy details. These patterns matter because aggregate labels can hide individual behavior.
Track disagreement by category. If labelers agree on simple FAQ answers but disagree on safety, relevance ranking, bias, or tone, the average agreement rate is hiding the part of the work that needs attention.
Test the guideline, too. Rewrite instructions, add anchor examples, change the scale, or split one vague label into two clearer dimensions. Then measure whether agreement and downstream model quality improve.
The value of a labeler is not just speed or cost per label. It is the amount of reliable, decision-useful signal they add to the evaluation or training process.

## High-Stakes Examples

### Example: TunedSearch


> Rate results for "can I mix ibuprofen and blood pressure medicine".

A cheap generic labeler may reward the result with the clearest wording. A medical reviewer may notice that the page overgeneralizes, misses contraindications, or should push the user toward a clinician or pharmacist. Both raters are doing a task, but only one may be measuring the product risk that matters.

Labeler value is not clicks per hour. It is whether the labels improve the system's judgment on the cases users can get hurt by.

The eval should compare labelers by downstream value: which rater group produces labels that reduce bad top results, policy failures, and unsafe summaries on future medical-adjacent queries?


## Expert Notes

When the system matters, measure marginal labeler value. Compare one-rater, two-rater, three-rater, and expert-adjudicated labels against downstream model ranking, judge calibration, release decisions, and production outcomes. Stop buying labels that make the dataset larger but not more trustworthy.
