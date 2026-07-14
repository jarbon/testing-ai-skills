# Section 29: Human Calibration of LLM Judges

**Book location:** Chapter 5, Judges, Humans, and Disagreement  
**Use when:** LLM judge, human calibration, human review, human calibration llm judges  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Before relying on an LLM judge at scale, builders need to know whether it scores like a trusted
human reviewer.

## Actions

- Compare it against the old judge.
- Check for overfitting to the examples.
- Watch slices where the fine-tuned judge becomes more confident but less correct.
- Treat judge quality as something you test, not something you assume.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for LLM judge, human calibration, human review, human calibration llm judges needed to reproduce work on Human Calibration of LLM Judges.
- Report results for LLM judge, human calibration, human review, human calibration llm judges by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

LLM judges need calibration because they are evaluators, not truth machines. Calibration checks whether the judge scores like trusted human reviewers on the cases that matter.
For example, a judge may reward polished writing while missing a subtle policy contradiction. Calibration makes that weakness visible before the judge is used at scale.

LLM judges can make large-scale evaluation possible, but they need calibration.

The central question is simple: does the judge score outputs the way our best human reviewers would?

The answer can be yes, at least in some settings. LLM judges are not just a toy; they can approximate human preference well enough to be operationally useful when the task, rubric, examples, and calibration process are strong.

But that possibility is not universal permission. A judge that tracks human preference on chatbot comparisons may still fail on your legal policy, medical summary, internal coding standard, safety rule, or domain-specific support workflow.

Without calibration, an LLM judge may be too lenient, too harsh, inconsistent, biased toward fluent writing, weak on domain-specific policy, or overly impressed by confident language. If you scale an uncalibrated judge, you may scale the wrong judgment.

A calibration process starts with a sample of outputs. Human reviewers score those outputs using the same rubric as the LLM judge. Then the team compares human scores with judge scores. Where did they agree? Where did they disagree? Were the disagreements random, or did they reveal a pattern?


For example, the LLM judge may give high scores to answers that are polite and well written but subtly contradict policy. That suggests the rubric or judge prompt needs to emphasize policy compliance more strongly. The judge may over-penalize brief answers even when they are correct. That suggests the rubric should clarify when concision is acceptable.

Disagreement can also reveal that the humans need alignment. If expert reviewers disagree often, the problem may not be the judge. The rubric may be vague, the policy may be ambiguous, or the examples may be genuinely borderline.


Calibration improves when rubrics include examples. Show what a 10 looks like. Show what a 7 looks like. Show what a 3 looks like. Show hard failures that should receive very low scores regardless of tone. Concrete examples help both humans and LLM judges apply the criteria more consistently.

Calibration is not only a report. It should change the judge system.

The first fix is usually the cheapest: add calibrated examples to the judge prompt. If humans score a CartCare refund answer as a 4 because it sounds friendly but violates policy, put that example in the prompt. If humans score a short answer as a 9 because it is correct, safe, and clear, include that too. The judge needs to see examples where tone, completeness, policy, source faithfulness, and safety trade off against each other.

The second fix is the rubric. If humans and the LLM judge disagree because the rubric says "helpful" but does not say whether policy beats warmth, rewrite the rubric. If the judge keeps rewarding long answers, add an anchor that says brevity is acceptable when the answer is complete. If the judge misses hard blockers, separate blocker checks from ordinary score dimensions.

The third fix is post-hoc calibration. Sometimes the LLM judge is directionally useful but consistently too generous or too harsh. In that case, do not pretend the raw score is the final score. Learn a calibration function from human-reviewed examples. For example, if human reviewers usually treat the judge's 9 as a human 7 on privacy-sensitive cases, the release report can apply a slice-specific discount:

```text
calibrated_score = raw_judge_score - privacy_slice_discount
```

That does not make the judge smarter. It makes the measurement more honest. More mature teams can use a calibration table, regression model, or isotonic calibration curve that maps raw judge scores to expected human scores by category. The important rule is that the mapping must be learned from held-out human-reviewed data, versioned, and rechecked when the judge model, prompt, rubric, policy, or product changes.

The fourth fix is routing. Calibration should tell you which cases the judge can handle and which cases need escalation. A judge might be reliable on low-risk style checks, acceptable on ordinary support answers, weak on medical advice, and unacceptable on policy edge cases. That means the output of calibration is not merely "judge accuracy." It is a routing policy: auto-score these cases, sample-audit those cases, send these slices to humans, and block release on these failures.

Fine-tuning is the expensive fix. If the team has enough high-quality human-reviewed examples, and the judge task is stable, fine-tuning a judge model can help it internalize local policy, domain language, and scoring preferences. But fine-tuning a judge also creates a new model to validate. Keep a holdout set. Compare it against the old judge. Check for overfitting to the examples. Watch slices where the fine-tuned judge becomes more confident but less correct.

Calibration should not be a one-time event. Model behavior changes, product policy changes, and evaluation needs change. Periodic calibration keeps the judge aligned with the product's current definition of quality.

Perfect agreement is unnecessary. What matters is knowing where the judge is reliable, where it is weak, and which cases need human escalation.

LLM judges are powerful when calibrated. Treat judge quality as something you test, not something you assume.

## Examples

### Example: CartCare Chatbot


> "I'm furious. Your driver left my $312 order in the rain, including my insulin. Refund me now or I'm posting this everywhere."

An uncalibrated LLM judge may give a high score to a warm, apologetic answer because it sounds empathetic. But the real quality bar is stricter.

Before trusting the judge, give it anchor examples.

A 10-point answer should:

- recognize the medical-risk item
- avoid promising a refund before checking policy and order state
- escalate because insulin is safety-sensitive and high-dollar
- explain the next step clearly
- preserve a calm tone without sounding evasive
- avoid blaming the driver or the customer

A 6-point answer might apologize and offer a generic refund path, but miss the medical escalation.

A 3-point answer might sound friendly but approve the refund without checking the order, policy, or fraud signals.

A 0-point answer might argue with the customer, ignore the insulin, or leak internal policy language.

Then run the LLM judge against known examples and compare it to human reviewers. If the judge keeps rewarding warmth over operational correctness, adjust the rubric, add better anchor examples, or discount that judge's scores for high-risk support cases.

The calibration question is not, "Did the judge give a score?" It is, "Does this judge reward the same things the business, policy, and user risk actually require?"


## Expert Notes

In production work, track judge-human agreement over time, by category, and by severity. A judge can be acceptable for low-risk style checks and unacceptable for regulated policy decisions. Calibration should produce routing rules, not just a single accuracy number.
