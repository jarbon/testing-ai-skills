# Section 88: Dataset Bias and Coverage Gaps

**Book location:** Chapter 12, Data, Bias, Raters, and Incentives  
**Use when:** RAG, dataset bias, dataset bias coverage gaps  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A clean-looking evaluation can still be wrong if the sample misses the people, languages, risks,
and workflows that matter.

## Actions

- Define runnable checks that exercise RAG, dataset bias, and dataset bias coverage gaps.
- Set acceptable outcomes and blocker failures for RAG, dataset bias, and dataset bias coverage gaps before running the evaluation.
- Run representative cases for RAG, dataset bias, and dataset bias coverage gaps and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for RAG, dataset bias, dataset bias coverage gaps needed to reproduce work on Dataset Bias and Coverage Gaps.
- Report results for RAG, dataset bias, dataset bias coverage gaps by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Dataset bias happens when the evaluation sample does not represent the real product problem. Coverage gaps are the places the test data simply does not reach.

For example, a support bot may perform well on English desktop refund questions and fail on Spanish mobile billing questions. The overall score can look fine while important users are underserved.

Every sample tells a story about the population it came from. If the sample is mostly easy, common, English-language, happy-path cases, the results describe that world. They do not describe the whole product.

Coverage gaps often hide in plain sight: languages, regions, accessibility needs, product tiers, customer segments, prompt lengths, device types, new users versus power users, and high-risk policy categories.

Bias also appears in labels. If reviewers are not trained on regional language, domain policy, disability access, or local expectations, the evaluation may reward the wrong behavior.

The fix starts with a coverage map. List the important segments and risks. Decide which ones need representative sampling and which ones need targeted stress tests. Then report results by segment.

Averages should never be allowed to erase vulnerable or high-impact groups. A model that performs well overall but fails a protected, regulated, or strategically important segment is not simply "mostly good."

Dataset quality is not administrative housekeeping. It is the foundation of whether the evaluation can be trusted.

## Case Study: Ariane 5 Flight 501

In 1996, Ariane 5 Flight 501 was destroyed shortly after launch because software reused from Ariane 4 failed under Ariane 5's different flight conditions. The software was not random. It was not "AI weird." It was deterministic code doing exactly what it had been built to do, just outside the assumptions that made it safe before.

The failure came from an inertial reference value that overflowed during conversion. On Ariane 4, that value stayed within range. On Ariane 5, the trajectory was different enough that the old assumption broke. Reuse made the system feel safer than it was.

That is the AI coverage lesson. A model, prompt, retrieval index, tool workflow, fine-tune, or judge can pass yesterday's eval suite and still fail when the product moves into a new distribution. New users, new policies, new documents, new geography, new hardware, new latency, new tool permissions, or new input style can push the system outside the envelope your tests actually covered.

Coverage analysis should not only ask, "Do we have lots of tests?" It should ask, "Do our examples still cover the operating envelope we are about to enter?" If the operating envelope changed, the eval suite has to change too. Otherwise, you are testing Ariane 5 with Ariane 4 confidence.

Source: [ESA Ariane 501 Inquiry Board report summary](https://www.esa.int/Newsroom/Press_Releases/Ariane_501_-_Presentation_of_Inquiry_Board_report)

## Expert Notes

At scale, maintain a coverage matrix with population share, risk weight, sample count, pass rate, confidence interval, known exclusions, label quality, and production drift. Make omissions explicit instead of letting them become hidden assumptions. A small but high-risk slice may deserve more samples than its traffic share would suggest.
