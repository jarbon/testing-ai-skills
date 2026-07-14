# Judges, Humans, and Disagreement

**Book location:** Chapter 5  
**Use when:** exact assertions, LLM judge, rubric, human calibration, human review, human calibration llm judges, evaluation criteria, inter-rater agreement, attention, inter rater agreement, topical entropy, disagreement diversity topical entropy, precision, rubrics actually work  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Use traditional testing techniques wherever they still work: exact assertions, schema checks, unit tests, component tests, static analysis, deterministic policy checks, citation-presence checks, and simple counters.
- Save LLM judges for the parts of quality that are genuinely semantic, fuzzy, contextual, or hard to express as deterministic code.
- Use deterministic checks first when the quality rule can be written down exactly.
- Use one calibrated LLM judge when the judgment is semantic and the risk is moderate.
- Use human review for severe failures, ambiguous cases, policy boundaries, and samples used to calibrate the judge.
- Compare it against the old judge.
- Check for overfitting to the examples.
- Watch slices where the fine-tuned judge becomes more confident but less correct.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [028 LLM-as-a-Judge](ch028-llm-judge.md)
- [029 Human Calibration of LLM Judges](ch029-human-calibration-llm-judges.md)
- [030 Inter-Rater Agreement](ch030-inter-rater-agreement.md)
- [031 Disagreement, Diversity, and Topical Entropy](ch031-disagreement-diversity-topical-entropy.md)
- [032 Rubrics That Actually Work](ch032-rubrics-actually-work.md)
- [033 Using Raters Well](ch033-raters.md)
- [034 Testing the Value of Data Labelers](ch034-value-data-labelers.md)
- [035 Data Labeling Dangers and Labeler Demographics](ch035-data-labeling-dangers-labeler-demographics.md)
