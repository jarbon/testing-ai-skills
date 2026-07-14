# Section 30: Inter-Rater Agreement

**Book location:** Chapter 5, Judges, Humans, and Disagreement  
**Use when:** evaluation criteria, LLM judge, inter-rater agreement, rubric, attention, inter rater agreement  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

When reviewers disagree often, the evaluation system may need as much attention as the product
being evaluated.

## Actions

- Define runnable checks that exercise evaluation criteria, LLM judge, and inter-rater agreement.
- Set acceptable outcomes and blocker failures for evaluation criteria, LLM judge, and inter-rater agreement before running the evaluation.
- Run representative cases for evaluation criteria, LLM judge, and inter-rater agreement and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for evaluation criteria, LLM judge, inter-rater agreement, rubric needed to reproduce work on Inter-Rater Agreement.
- Report results for evaluation criteria, LLM judge, inter-rater agreement, rubric by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Inter-rater agreement measures whether reviewers apply the evaluation criteria consistently. Reviewers can be humans, LLM judges, or both.
For example, if one reviewer scores an answer 9 and another scores it 3, the issue may be the output, the rubric, the policy, or reviewer training.

Inter-rater agreement measures whether multiple reviewers agree. The reviewers may be humans, LLM judges, or a combination of both.

Agreement matters because evaluation is only useful if the criteria can be applied consistently. If one reviewer scores an answer 9 and another scores it 3, the team needs to understand why.

Disagreement can mean several things. The rubric may be vague. The product policy may be unclear. The output may be genuinely borderline. One reviewer may be too strict. Another may be too lenient. An LLM judge may be biased toward confident writing or may miss domain-specific details.

You do not need advanced statistics to begin tracking agreement. Start simply. Have three reviewers score 100 outputs. Count how often all reviewers agree, how often two agree, and how often all disagree. Then review the disagreement cases.

The value is in the discussion. If reviewers disagree because the policy is unclear, the product team may need to clarify the policy. If they disagree because the rubric does not define "complete" or "safe" precisely enough, the rubric needs improvement. If they disagree only on borderline cases, those cases may need escalation rules.

More advanced teams can use measures such as [Cohen's kappa](https://en.wikipedia.org/wiki/Cohen%27s_kappa) or [Krippendorff's alpha](https://en.wikipedia.org/wiki/Krippendorff%27s_alpha). These statistics adjust for agreement that might happen by chance. They can be useful, especially when evaluation becomes part of a formal release process. But they are not required to get started.

## Cohen's Kappa

[Cohen's kappa](https://en.wikipedia.org/wiki/Cohen%27s_kappa) is useful when two raters label the same items with categories, such as safe/unsafe, relevant/not relevant, grounded/hallucinated, or escalate/do not escalate. It answers a better question than raw agreement: how much did the two raters agree after subtracting the agreement they might have gotten by chance?

The formula is:

```text
kappa = (observed_agreement - expected_chance_agreement) / (1 - expected_chance_agreement)
```

Suppose two reviewers label 100 CartCare answers as either acceptable or risky. Reviewer A is shown in the rows; Reviewer B is shown in the columns:

|  | B: acceptable | B: risky |
| --- | ---: | ---: |
| A: acceptable | 50 | 10 |
| A: risky | 10 | 30 |

They agree on 80 of 100 cases, so raw agreement is 0.80. That sounds strong, but some agreement would happen just because both reviewers use "acceptable" and "risky" at similar rates.

Reviewer A says acceptable 60 times and risky 40 times. Reviewer B also says acceptable 60 times and risky 40 times. The expected chance agreement is:

```text
expected_chance_agreement =
  (A_acceptable_rate * B_acceptable_rate) +
  (A_risky_rate * B_risky_rate)

expected_chance_agreement =
  (0.60 * 0.60) + (0.40 * 0.40) = 0.52
```

Now calculate kappa:

```text
kappa = (0.80 - 0.52) / (1 - 0.52)
kappa = 0.28 / 0.48
kappa = 0.58
```

That is a more sober result than "80% agreement." The raters agree more than chance, but the evaluation system is not perfectly calibrated. For a low-risk style check, 0.58 might be usable with spot review. For privacy, medical, financial, or legal decisions, it should trigger more rubric work, reviewer training, or escalation.

Kappa is also sensitive to label prevalence. If almost every case is "acceptable," raw agreement can look high while kappa stays modest. That is not a bug in the statistic; it is a warning that the dataset may not contain enough hard or risky cases to prove the reviewers are aligned.

## Krippendorff's Alpha

[Krippendorff's alpha](https://en.wikipedia.org/wiki/Krippendorff%27s_alpha) is useful when the review setup is messier: more than two raters, missing ratings, ordinal scores, interval scores, or mixed reviewer coverage. That makes it a better fit for many real AI evaluation programs, where not every reviewer scores every item and where some labels are 0-10 scores instead of simple yes/no categories.

The intuition is similar to kappa:

```text
alpha = 1 - (observed_disagreement / expected_disagreement)
```

Observed disagreement asks: how often did reviewers assigned to the same item disagree? Expected disagreement asks: how much disagreement would we expect if labels were paired randomly from the overall label pool?

For a simple nominal example, imagine three reviewers label five TunedSearch results as safe or risky:

```text
Item 1: safe,  safe,  safe
Item 2: risky, risky, risky
Item 3: safe,  safe,  risky
Item 4: safe,  risky, risky
Item 5: safe,  safe,  safe
```

Each item has three reviewer pairs. Items 1, 2, and 5 have no pairwise disagreement. Item 3 has two disagreeing pairs. Item 4 also has two disagreeing pairs. Across all 15 reviewer pairs, 4 pairs disagree:

```text
observed_disagreement = 4 / 15 = 0.27
```

Across all labels, reviewers used safe 9 times and risky 6 times. If labels were paired randomly, the expected disagreement rate is about:

```text
expected_disagreement =
  2 * safe_count * risky_count / (total_labels * (total_labels - 1))

expected_disagreement =
  2 * 9 * 6 / (15 * 14) = 0.51
```

Now calculate alpha:

```text
alpha = 1 - (0.27 / 0.51)
alpha = about 0.48
```

That result says the reviewers agree better than random labeling, but not well enough to treat the labels as a stable release signal. The next step is not to worship the number. The next step is to inspect Items 3 and 4. Did reviewers disagree because the result was ambiguous? Because the policy was unclear? Because one reviewer noticed a safety issue the others missed? That investigation is the real value.

For ordinal 0-10 scores, Krippendorff's alpha can give partial credit when reviewers are close. A 7 versus 8 disagreement is not the same as a 2 versus 9 disagreement. That is one reason it is useful for AI quality rubrics, where reviewers may not produce identical scores but still agree on the practical decision.

Inter-rater agreement also helps calibrate LLM judges. If the LLM judge agrees with expert humans on clear cases but struggles on ambiguous policy boundaries, Confidence Engineers know where to add human review.

The key insight is that disagreement is not just noise. It is information. It tells you where the evaluation system is unclear, where the product behavior is ambiguous, and where automated judgment may be risky.

If good reviewers cannot agree, the system may not be the only thing that needs fixing. The definition of quality may need work too.

## Examples

### Example: CartCare Chatbot


> "My child drank spoiled milk from yesterday's delivery. What should I do?"

Three raters score the same answer. One gives it a 9 because the tone is calm. One gives it a 5 because it should have escalated. One gives it a 2 because the bot gave medical-sounding advice without a policy source.

That disagreement is not just noise. It tells you the rubric does not clearly separate tone, medical risk, food-safety policy, and escalation. Before using those labels to train or judge the system, calibrate the raters on anchor examples and decide which mistakes are blockers.

Raw agreement asks whether raters match. Good measurement asks why they do not.


## Expert Notes

Expert teams use agreement statistics carefully. [Cohen's kappa](https://en.wikipedia.org/wiki/Cohen%27s_kappa), [Fleiss' kappa](https://en.wikipedia.org/wiki/Fleiss%27_kappa), and [Krippendorff's alpha](https://en.wikipedia.org/wiki/Krippendorff%27s_alpha) adjust for chance agreement, but they still depend on label design, prevalence, reviewer training, and whether the task is ordinal or categorical.
