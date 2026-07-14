# Data, Bias, Raters, and Incentives

**Book location:** Chapter 12  
**Use when:** RAG, dataset bias, dataset bias coverage gaps, bias data, bias labeling, benchmark, bias training, NDCG, latency, bias productization, bias taxonomy, language bias, cultural language bias, accessibility bias  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Define runnable checks that exercise RAG, dataset bias, and dataset bias coverage gaps.
- Set acceptable outcomes and blocker failures for RAG, dataset bias, and dataset bias coverage gaps before running the evaluation.
- Run representative cases for RAG, dataset bias, and dataset bias coverage gaps and preserve the failures that would change the decision.
- Track provenance, sampling windows, exclusion rules, coverage gaps, leakage between train and test sets, and feedback loops from production behavior.
- Define runnable checks that exercise bias data.
- Set acceptable outcomes and blocker failures for bias data before running the evaluation.
- Ask multiple raters to label the same item, then measure where they agree and where they diverge.
- Use agreement metrics, entropy analysis, rater demographics, guideline A/B tests, and adjudication logs.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [088 Dataset Bias and Coverage Gaps](ch088-dataset-bias-coverage-gaps.md)
- [089 Testing Bias in Data](ch089-bias-data.md)
- [090 Testing Bias in Labeling](ch090-bias-labeling.md)
- [091 Testing Bias in Training](ch091-bias-training.md)
- [092 Testing Bias in Productization](ch092-bias-productization.md)
- [093 Bias Taxonomy for AI Systems](ch093-bias-taxonomy.md)
- [094 Cultural and Language Bias in AI](ch094-cultural-language-bias.md)
- [095 Socioeconomic and Accessibility Bias](ch095-socioeconomic-accessibility-bias.md)
- [096 Measuring Bias with Slices, Counterfactuals, and Raters](ch096-measuring-bias-slices-counterfactuals-raters.md)
- [097 Bias in Deployment, Feedback Loops, and Productization](ch097-bias-deployment-feedback-loops-productization.md)
- [098 Survivorship Bias in AI Quality](ch098-survivorship-bias-quality.md)
