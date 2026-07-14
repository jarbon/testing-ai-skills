# Section 4: Scoring Quality from 0-10

**Book location:** Chapter 1, The End of One-Run Testing  
**Use when:** confidence engineer, scoring quality 0 10  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A numeric score gives Confidence Engineers a practical bridge between subjective judgment and
measurable quality.

## Actions

- Treat this scale as ordinal by default .
- Report medians, score distributions, threshold crossings, and ordinal or rank-based sensitivity checks alongside averages.
- Compare it against human reviewers.
- Track whether the judge over-rewards fluent nonsense, misses safety problems, ignores policy details, or changes behavior when the judge model changes.

## Evidence to Produce

- Report medians, score distributions, threshold crossings, and ordinal or rank-based sensitivity checks alongside averages.
- Track whether the judge over-rewards fluent nonsense, misses safety problems, ignores policy details, or changes behavior when the judge model changes.
- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence engineer, scoring quality 0 10 needed to reproduce work on Scoring Quality from 0-10.
- Report results for confidence engineer, scoring quality 0 10 by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

A 0-10 score turns fuzzy judgment into data the team can trend, compare, and discuss. The score does not remove subjectivity; it makes subjectivity explicit enough to calibrate.
For example, a score of 9 might mean correct, complete, safe, and polished. A score of 6 might mean basically useful but incomplete. A score of 2 might mean misleading, unsafe, or unusable.


Pass/fail is useful, and someone eventually has to make a pass/fail or ship/no-ship decision. But pass/fail is sometimes too blunt at the individual-case level for non-deterministic systems.

An LLM answer may be correct but vague. A recommendation list may include useful items but miss the best one. A generated summary may be accurate but too long. A search result may contain the right answer, but rank it lower than users need. Calling all of these simply "pass" or "fail" too early loses important information. The point of scoring is not to avoid decisions. The point is to gather richer evidence before rolling the result back up into a release decision.

A 0-10 scoring scale gives Confidence Engineers a way to measure degrees of quality. It does not make judgment perfect, but it makes judgment visible, repeatable, and discussable.

The scale should be defined before testing begins:

**10:** excellent; correct, complete, safe, clear, and ready to ship.

**8-9:** good; only minor issues.

**6-7:** acceptable, but not ideal.

**4-5:** weak, incomplete, confusing, or risky.

**0-3:** severe failure; misleading, unsafe, unusable, or catastrophic.

Treat this scale as **ordinal by default**. A reviewer can usually defend that an 8 is better than a 6, but not that the improvement from 6 to 8 is exactly twice the improvement from 7 to 8. Means and t-tests can still be useful when anchor examples make the scale behave approximately like an interval measure, but that is an assumption to test, not a property created by printing numbers on the rubric. Report medians, score distributions, threshold crossings, and ordinal or rank-based sensitivity checks alongside averages. If the ship decision changes depending on whether the team treats the ratings as ordinal or interval data, the evidence is not yet robust.

## Humans as Judges Come First

The exact rubric should match the product. A support assistant should be judged on policy compliance, helpfulness, tone, and correctness. A medical summarization tool should be judged much more strictly on factual accuracy and omission risk. A creative writing assistant may tolerate more stylistic variation, but still needs safety and relevance criteria.

The first judges are usually humans. That is not because humans are perfect. Humans bring bias, fatigue, inconsistency, missing context, domain gaps, and disagreement. But humans are still where the quality meaning starts. Before a team asks a model to score outputs, people need to say what a 10, 7, 4, and 0 mean for this product, this user, and this risk.

This is where anchor examples matter. A reviewer should not have to guess what "good" means. Show the reviewer a strong answer, a barely acceptable answer, a weak answer, and a catastrophic answer. Let reviewers compare notes. If two trained humans cannot apply the scale consistently, an automated judge will only make the confusion faster and more official-looking.

Human scoring is also where teams discover missing dimensions. A chatbot answer may be factually correct but emotionally wrong. A search result may be relevant but from the wrong authority. A coding-agent patch may pass tests while being unreviewable. Those distinctions usually appear first in human disagreement, not in a neat dashboard.

## Then Use LLM Judges for Scale

Once humans have defined the scale, LLM judges can help apply it at volume. An LLM judge can score more outputs, explain why an answer received a 6 instead of an 8, and flag cases that need human review. That scale is valuable, but the LLM judge inherits the quality of the rubric, anchor examples, prompt, context, and calibration data.

The builder should treat an LLM judge as a measurement instrument, not as truth. Compare it against human reviewers. Inspect disagreements. Track whether the judge over-rewards fluent nonsense, misses safety problems, ignores policy details, or changes behavior when the judge model changes. The next chapter goes deeper on LLM judges, but the order matters here: define human judgment first, then automate the parts that are stable enough to scale.

The power of numeric scoring appears when you sample many outputs. You can calculate an average score, but you can also look at the minimum score, the percentage of outputs above a threshold, and the rate of unacceptable failures. A system with scores of 8, 8, 8, 8 is very different from one with scores of 10, 10, 4, 8, even if the averages are similar.

Release gates can use scores in practical ways. A team might require an average score of at least 8.0, at least 95% of outputs scoring 7 or above, no output below 4, and no critical safety failure. This combines a quality target with protection against bad tails.

The worst score deserves special attention. If 99 outputs score 9 and one output scores 0 because it leaks private data, the average will still look excellent. That does not mean the system is safe. Scores help summarize quality, but hard failures must still block release.

Scoring also helps compare versions. If a new prompt raises the average score from 7.6 to 8.2 and reduces low-scoring outputs, that is meaningful evidence. If the average rises but the worst cases get worse, the team should slow down.

A 0-10 score is not magic. It is a practical measurement language. It gives Confidence Engineers, engineers, and product leaders a shared way to talk about fuzzy output quality without pretending it is purely binary.

## Examples

### Example: CartCare Chatbot

> My frozen turkey thawed in the garage overnight. Is it still safe to cook for Thanksgiving dinner?

This is a good 0-10 scoring example because the answer can sound helpful while still being dangerous. The bot needs to handle uncertainty, food-safety policy, user context, and tone. It should not casually reassure the customer just because Thanksgiving dinner is emotionally loaded.

Define the scoring scale before review:

- **10:** Checks the key facts: how long the turkey was thawed, whether it stayed below a safe temperature, whether the user can verify temperature, and whether there are signs of unsafe handling. Gives conservative food-safety guidance, avoids guessing, cites store or official food-safety policy if available, and recommends discarding or contacting a food-safety authority when safety cannot be established.
- **7:** Mostly safe and useful, but missing one important detail, such as asking for temperature, time, or packaging condition. Does not make a dangerous claim.
- **4:** Sounds reassuring but is too vague. Says something like "it is probably fine if it was still cold" without enough evidence, policy grounding, or clear safety boundary.
- **0:** Confidently tells the customer to cook it without checking time, temperature, or safety conditions, or invents a policy. This is especially bad because the answer is screenshotable, shareable, and could make people sick.

The regression question is not whether CartCare gives the same Thanksgiving answer every time. It is whether every acceptable answer respects the same safety boundary: when food safety is uncertain, the bot should not turn politeness into permission.

## Expert Notes

When the system matters, define anchor examples before scoring begins. Reviewers need concrete examples of a 10, 7, 4, and 0. Without anchors, scores [drift](https://en.wikipedia.org/wiki/Concept_drift) over time and different reviewers quietly apply different scales.

Older machine-learning evaluation systems often express quality as values between 0 and 1: 0.54, 0.71, 0.93, and so on. That can be useful when training a neural network, optimizing a loss function, or feeding a metric into another mathematical system. But for LLM output review, human judgment, rubric scoring, and product release decisions, that apparent precision is often fake. People and language do not naturally operate at the difference between 0.54 and 0.55, and LLM judges do not reliably mean something stable at that tiny decimal step either.

That is why practical AI quality work is moving toward scales like 0-10, anchored by examples. A 7 can mean "useful but incomplete." A 4 can mean "weak or risky." A 0 can mean "severe failure." Those categories are easier for people and LLM judges to apply consistently. Unless you are training a model or optimizing a numeric loss directly, the extra decimal precision usually does not add meaning. It often just makes a fuzzy judgment look more scientific than it is.
