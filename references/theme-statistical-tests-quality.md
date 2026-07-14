# Statistical Tests for AI Quality

**Book location:** Chapter 4  
**Use when:** t-test, p-value, statistical significance, paired data, compare prompt or model versions, null hypothesis, null hypothesis we actually, chi-squared, chi squared tests categorical quality, p values evidence permission, confidence engineer, statistical significance practical significance, sample size, power analysis  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Use judgment and risk analysis to decide whether the improvement is safe and worth shipping.
- Start with the data-generating process, not a favorite test.
- Ask what the experimental unit is, whether the same units saw both versions, what kind of outcome was measured, and which observations can influence one another.
- Compare versions within prompt, summarize or model the repeated runs, and calculate uncertainty at the prompt or cluster level.
- Define runnable checks that exercise null hypothesis and null hypothesis we actually.
- Set acceptable outcomes and blocker failures for null hypothesis and null hypothesis we actually before running the evaluation.
- Run representative cases for null hypothesis and null hypothesis we actually and preserve the failures that would change the decision.
- Use chi-squared tests when the outcome is categorical: pass or fail, safe or unsafe, grounded or hallucinated, answer or refuse, correct tool or wrong tool, satisfied or escalated.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [020 Comparing Versions with t-tests](ch020-compare-versions-t-tests.md)
- [021 Null Hypothesis: What Are We Actually Testing?](ch021-null-hypothesis-we-actually.md)
- [022 Chi-Squared Tests for Categorical AI Quality](ch022-chi-squared-tests-categorical-quality.md)
- [023 P-Values: Evidence, Not Permission](ch023-p-values-evidence-permission.md)
- [024 Statistical Significance vs. Practical Significance](ch024-statistical-significance-practical-significance.md)
- [025 Power Analysis and Minimum Detectable Effect](ch025-power-analysis-minimum-detectable-effect.md)
- [026 Multiple Comparisons and False Discoveries](ch026-multiple-comparisons-false-discoveries.md)
- [027 F-Scores, Precision, Recall, and AI Quality](ch027-f-scores-precision-recall-quality.md)
