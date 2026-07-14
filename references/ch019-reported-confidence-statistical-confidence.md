# Section 19: AI-Reported Confidence vs. Statistical Confidence

**Book location:** Chapter 3, Sampling and Uncertainty  
**Use when:** confidence interval, statistical confidence, RAG, reported confidence statistical confidence  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

An LLM saying it is confident is not the same as a confidence interval calculated from sample
data.

## Actions

- Treat them differently, report them differently, and never let model confidence pretend to be proof.
- Choose thresholds on held-out data using the cost of mistakes.
- Report quality together with coverage , the fraction of cases the system chose to answer.
- Use it when the output and error event are defined precisely enough to calibrate.
- Do not publish one global calibration number without slice counts and freshness.

## Evidence to Produce

- Report quality together with coverage , the fraction of cases the system chose to answer.
- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence interval, statistical confidence, RAG, reported confidence statistical confidence needed to reproduce work on AI-Reported Confidence vs. Statistical Confidence.
- Report results for confidence interval, statistical confidence, RAG, reported confidence statistical confidence by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

This chapter separates two meanings of confidence that sound similar but behave very differently. One comes from a model's self-assessment. The other comes from measured results across many examples.

A useful mental shortcut is this: model confidence is a claim made by the system, while statistical confidence is evidence gathered about the system. Builders should be much more cautious about the first than the second.

## Overview

AI-reported confidence and statistical confidence are different things. An LLM's confidence is a self-assessment of a single judgment. Statistical confidence comes from sample data and observed variation.
For example, a judge may say it is highly confident that one answer deserves an 8. That does not tell you the true average quality of the whole system.

LLMs can report confidence, but that confidence should not be confused with statistical confidence.

An LLM judge might evaluate an answer and say, "Score: 8 out of 10. Confidence: medium. Likely score range: 7 to 9." That can be useful. It tells the Confidence Engineer that the judge found the case somewhat ambiguous or that the score might depend on interpretation.

But that is not a statistical confidence interval. It is a model's self-reported sense of certainty. Models can be overconfident. They can be underconfident. They can sound certain while being wrong. Their confidence may not be calibrated to real-world accuracy unless you test it.

Statistical confidence comes from sample data. If you score 100 outputs and calculate a mean score of 8.2 with a 95% confidence interval from 7.8 to 8.6, that interval is based on observed variation and sample size. It is a calculation, not a self-assessment.

Both forms of confidence can be useful, but they answer different questions. AI-reported confidence helps prioritize review. Low-confidence judgments may deserve human attention because the case is ambiguous. Statistical confidence helps estimate system behavior across a sample.

A good evaluation report labels them clearly. It might say: the LLM judge scored this individual output 8 out of 10 with medium confidence. Across 100 outputs, the observed mean was 8.2 with a 95% confidence interval of 7.8 to 8.6.

The first statement is about one judgment. The second statement is about measured performance across a sample.

Calibration is important. If an LLM judge says it is highly confident on cases where human experts often disagree, that confidence is not very useful. Confidence Engineers should periodically compare judge confidence and judge scores against human review.

The safest rule is simple: AI confidence is a signal. Statistical confidence is a calculation. Treat them differently, report them differently, and never let model confidence pretend to be proof.

## Calibration and Abstention

A confidence score becomes useful only when it is calibrated against observed outcomes. If a system labels 100 decisions as having 80% confidence, roughly 80 of those decisions should be correct under the definition and population being measured. A model that says 0.95 for nearly everything may sound decisive while providing almost no information about which cases are actually safe.

A **reliability diagram** makes this visible. Put predictions into confidence bands, such as 0.5-0.6, 0.6-0.7, and so on. For each band, compare average predicted confidence with the observed success rate. A well-calibrated system stays near the diagonal. A point below the diagonal is overconfident; a point above it is underconfident. Always include the count in each band. A nearly empty 0.9-1.0 band should not carry the same weight as a band containing half the traffic.

Two summary measures are common:

- **Brier score** is the mean squared difference between a predicted probability and the binary outcome: \(\frac{1}{n}\sum(p_i-y_i)^2\). Lower is better. It rewards probabilities that are both accurate and appropriately cautious.
- **Expected calibration error (ECE)** takes a weighted average of the gap between confidence and observed accuracy across bins. Lower is better, but the result depends on how the bins are chosen and can hide a badly calibrated high-risk slice.

Calibration should lead to an action policy, not just a prettier chart. Choose thresholds on held-out data using the cost of mistakes. A support bot might answer directly above 0.90, ask a clarifying question from 0.70 to 0.90, and route to a person below 0.70. A medical or financial workflow may need a much higher threshold and hard policy checks regardless of confidence. Recheck those thresholds after model, prompt, retrieval, or traffic changes.

This is **selective prediction**: the system is allowed to abstain. Report quality together with **coverage**, the fraction of cases the system chose to answer. A model that is 99% accurate because it answers only the easiest 5% of requests is not necessarily useful. Plot risk against coverage so the tradeoff is explicit.

Conformal prediction can provide prediction sets or intervals with a chosen empirical coverage under assumptions such as exchangeability between calibration and future data. It can be valuable for classification, extraction, and bounded numeric predictions. It is not a magic wrapper for arbitrary generated prose, and its guarantees can fail under distribution shift. Use it when the output and error event are defined precisely enough to calibrate.

The practical sequence is straightforward: define correctness, reserve calibration data, measure reliability by slice, choose answer and abstention thresholds from the real error costs, then monitor coverage and calibration after release. Confidence that cannot change system behavior is mostly decoration.

Calibration is local to a version, population, and decision. A score calibrated on English support questions may be badly calibrated on medical questions, long tool traces, another language, or next month's traffic. Do not publish one global calibration number without slice counts and freshness. Recalibrate after changes to the model, prompt, retriever, judge, or traffic mix, and keep the calibration set separate from threshold tuning so the team does not fit the confidence policy to its own exam.

## From the Field: Ask the Model Why It Is Unsure

An early trick I found with LLMs was to ask the model for its confidence along with the answer. At a conference, I used a simple example: ask an AI, "How many planets are in the solar system? Give me one integer."

It will give you an integer. But the question is messier than the prompt makes it sound. Pluto was reclassified as a dwarf planet, but not everyone thinks about the boundary the same way. Some people learned nine planets. Some learned eight. Some astronomers still argue about definitions. If you force the model to output only an integer, you hide the ambiguity and make the answer look cleaner than the world actually is.

If you instead ask for the answer plus confidence, the model will often tell you it is not perfectly certain. It may say the conventional answer is eight, then explain that the ambiguity comes from Pluto, definitions, and historical usage. That is useful. It lets the system say, "Here is my answer, but here is why the question is not as crisp as it looks."

This is one reason people sometimes think AI is worse than it is: they prompt it into a corner. They demand a single number, a single answer, a single JSON field, or a single yes/no decision when the honest answer has uncertainty, scope, and assumptions. Humans do the same thing when pressured. If you force an answer, you often get an answer-shaped object, not reliable evidence.

Real measured confidence would look very different. You might collect a recent sample of astronomy papers, textbooks, agency explainers, and classroom materials, then label how many treat the solar system as eight planets, nine planets, or something more nuanced. You could measure how often each answer appears, how much disagreement remains by source type, and how stable that pattern is over time. Then you could say something like, "In this sample, 92% of current astronomy sources use eight planets, with most disagreement coming from educational or historical material." That is evidence gathered from the world, not a model reporting how sure it feels.

But do not confuse that model-reported confidence with statistical confidence. The model's confidence is still a claim from the system. It may correlate loosely with correctness in some domains, especially when the model can see ambiguity in the prompt or knows the topic well. But it is not a confidence interval calculated from samples. It is not a release gate. It is not proof.

For production decisions, use measured data. Run samples. Compare outputs. Calculate intervals. Check calibration. Do not ask the system, especially a system evaluating itself, "How confident are you?" and then treat the answer as mathematical evidence. AI-reported confidence can help route review and expose ambiguity. Statistical confidence comes from measurement.


## Examples

### Example: TunedSearch


> "how many planets are in the solar system?"

The model may answer "eight" with high confidence. It may also mention Pluto, dwarf planets, or historical definitions. The self-reported confidence can be useful as a clue that the answer has ambiguity, but it is not statistical confidence.

Statistical confidence would come from repeated measurement: run the query across model versions, prompts, markets, and recent astronomy sources; score whether the answer is current, clear, and honest about the definition; then measure the distribution.

The test should keep the two claims separate:

- model confidence: "I think this answer is right"
- measured confidence: "In our sample, this behavior passed with this uncertainty"

Do not let the model grade its own certainty when the release decision needs measured evidence.


## High-Stakes Examples

## Expert Notes

Expert teams calibrate AI confidence. They check whether high-confidence judge decisions actually agree with expert humans more often than low-confidence decisions. If not, the confidence label is not useful for routing or release decisions.
