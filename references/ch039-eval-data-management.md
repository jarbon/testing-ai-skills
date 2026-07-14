# Section 39: Eval Data Management

**Book location:** Chapter 6, Building Evals That Matter  
**Use when:** rubric, trace, eval data management  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

If prompts, datasets, rubrics, labels, judges, and model versions are not versioned, the
evaluation cannot be trusted.

## Actions

- Define runnable checks that exercise rubric, trace, and eval data management.
- Set acceptable outcomes and blocker failures for rubric, trace, and eval data management before running the evaluation.
- Run representative cases for rubric, trace, and eval data management and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for rubric, trace, eval data management needed to reproduce work on Eval Data Management.
- Report results for rubric, trace, eval data management by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Eval data management is the discipline of keeping evaluation artifacts traceable. It sounds boring until a team cannot explain why last month's score and this month's score are different.
For example, a quality score can change because the model improved, the judge changed, the rubric changed, the sample changed, or labels were updated. Without versioning, those causes blur together.

Non-deterministic evaluation produces many artifacts: prompts, model versions, retrieval snapshots, datasets, labels, rubrics, judge prompts, judge models, scoring code, random seeds, traces, outputs, and reports.
Each artifact should have an identity. When a result is reported, the team should know exactly which versions produced it.
This matters for comparisons. If Version B used a different judge prompt than Version A, the comparison may not be fair. If the dataset changed, the trend line may be measuring sample drift instead of product quality.
Good eval data management also protects institutional memory. Production failures become golden cases. Rubric changes explain why older scores are not directly comparable. Label updates show how the team's definition of quality evolved.
Privacy and access controls belong here too. Eval datasets often contain real user examples or sensitive business policy. The team should know what can be stored, who can see it, and how long it is retained.
A credible evaluation is not just a score. It is a score with provenance.

### Example: TunedSearch: The Search Engine Improved Without Changing
The TunedSearch dashboard jumps from 78 to 86 overnight. Everyone assumes the new ranker is working. There is one awkward detail: no ranker, prompt, model, or production code was deployed.

The eval suite contains fast-changing queries such as:

- "What is the smartest open-source LLM right now?"
- "Did OpenAI just change API pricing?"
- "Which coding agent currently leads SWE-bench?"
- "What AI regulations take effect in California this year?"

While refreshing the eval, the team changed several things at once:

- Forty stale expected results were replaced.
- The retrieval snapshot was refreshed.
- The judge model was upgraded.
- The rubric reduced the penalty for weak citations.
- Twelve difficult queries were removed because reviewers could not agree on the answer.

The score improved, but the product did not. The team accidentally measured a friendlier test.

Every run should therefore identify the complete eval bundle: dataset version, labels, rubric, judge prompt, judge model, retrieval snapshot, scoring code, and product version. The dashboard should refuse to draw a continuous trend line across incompatible bundles.

The useful question is not "Why did the score increase?" It is "What changed in the product, and what changed in the instrument measuring it?"

## Expert Notes

Expert teams treat evals like experiments and production telemetry at the same time. They keep immutable run records, separate raw data from derived labels, document schema changes, and make comparisons only between compatible runs.
