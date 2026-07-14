# Section 35: Data Labeling Dangers and Labeler Demographics

**Book location:** Chapter 5, Judges, Humans, and Disagreement  
**Use when:** release gate, data labeling dangers labeler demographics  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The people and systems that create labels become part of the product's definition of quality.

## Actions

- Use overlap and agreement metrics for ambiguous cases.
- Use experts for high-risk domains, calibration sets, severe failures, and labels that define release gates.
- Use LLM labelers for scale only after calibrating them against humans who actually understand the domain.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for release gate, data labeling dangers labeler demographics needed to reproduce work on Data Labeling Dangers and Labeler Demographics.
- Report results for release gate, data labeling dangers labeler demographics by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Data labeling looks like a plumbing problem until it becomes a product-quality problem. Labels become training targets, evaluation truth, judge calibration data, relevance grades, safety categories, preference rankings, and release gates. If the labels are wrong, shallow, biased, inconsistent, or created by people who lack the needed context, the system learns and measures the wrong thing.

Labeler demographics matter. Labeler expertise matters. Labeler incentives matter. So do the instructions, pay rate, time pressure, fatigue, language, culture, geography, device, education, and lived context of the people doing the work. A careful labeler can still be the wrong measurement instrument for the task.

If you are building an AI system for medical decisions, you should be very cautious about relying on generic labelers with no clinical training to decide whether an answer is medically correct. They may try hard. They may search the web. They may follow guidelines. But they are not doctors, nurses, radiologists, pharmacists, or domain specialists. The same issue appears in law, finance, safety, education, national security, accessibility, and any domain where surface plausibility is not the same as expert judgment.

The hard part is cost. Expert labels are expensive. Doctors, lawyers, physicists, senior engineers, accessibility experts, and domain specialists cannot label every item in every dataset. That does not make generic labeling useless. It means teams need to know which labels can be safely delegated, which labels need expert review, and which labels should be treated as uncertain rather than ground truth.

Mechanized and LLM-powered labeling adds another layer. Automated labels can scale quickly, but they inherit the model's training data, cultural assumptions, safety tuning, blind spots, and bogus knowledge. If an LLM judge was trained or aligned on flawed human labels, it can reproduce those flaws with more confidence and less visible disagreement. Cheap labels can become expensive mistakes when they are treated as truth.

Bad labels also already live inside many models and datasets. Public training data includes errors, spam, propaganda, outdated facts, synthetic content, low-quality annotations, scraped labels, and hidden demographic skews. Fine-tuning and preference data can add more bias. The quality of that label data should be reviewed seriously, but in practice it often is not. Teams trust the dataset because it is large, the vendor is famous, or the benchmark looks official.

The practical failure mode is simple: the labeler pool becomes an invisible product requirement. If one broad rater population labels medical questions, legal answers, accessibility scenarios, local services, code changes, and consumer shopping tasks, the system will learn that population's limits as if they were truth. The fix is not to insult generic raters. The fix is to design the labeling plan by domain, risk, geography, language, user context, and expertise before the labels become training data.

That is not a criticism of labelers. It is a criticism of pretending labels are context-free. Labelers are part of the instrument. If the instrument is mismatched to the domain, the measurement is distorted.

## Examples

### Example: TunedSearch


> "best waterproof work boots for roofing in phoenix summer"

A rater who has never worked construction in extreme heat may reward glossy review sites. A roofer may care about traction, heat, ankle support, sole wear, and whether the boot survives tar and ladders. A desert worker may judge breathable materials differently from someone in Seattle.

If the rater pool is narrow, the engine learns that pool's idea of relevance. That is not evil. It is measurement bias.

The label record should preserve who rated the result, what expertise the task needed, and which user slice the label is supposed to represent. Otherwise, the training data silently turns one demographic's judgment into the product's judgment.


## Expert Notes

The deeper move is to treat labels as evidence with provenance, not as truth. Every important label should have a source: who or what produced it, under which guideline, with which expertise, in which context, at what time, with what disagreement, and with what adjudication path.

Use tiered labeling. Let inexpensive raters handle obvious low-risk cases. Use overlap and agreement metrics for ambiguous cases. Use experts for high-risk domains, calibration sets, severe failures, and labels that define release gates. Use LLM labelers for scale only after calibrating them against humans who actually understand the domain.

The core question is not "Can we get labels cheaply?" It is "What product behavior will these labels reward?" If the answer is "behavior preferred by a narrow, under-contextualized labeler pool," the model will optimize for that pool. Sometimes that is acceptable. Often it is exactly the bias the team needed to detect.
