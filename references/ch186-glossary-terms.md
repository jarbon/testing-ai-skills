# Section 186: Appendix: Glossary of AI Testing Terms

**Book location:** Appendices, Tools, Templates, and Reference  
**Use when:** glossary terms  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A shared vocabulary makes AI quality work easier to teach, debate, and improve.

## Actions

- Define runnable checks that exercise glossary terms.
- Set acceptable outcomes and blocker failures for glossary terms before running the evaluation.
- Run representative cases for glossary terms and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for glossary terms needed to reproduce work on Appendix: Glossary of AI Testing Terms.
- Report results for glossary terms by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

A glossary is not filler. It is infrastructure for shared understanding. AI quality work mixes testing, statistics, machine learning, security, product, and operations.
When people use the same words differently, eval discussions become confusion disguised as alignment.

Non-deterministic system: a system whose behavior can vary across runs, inputs, contexts, versions, or hidden state.
Sample: a subset of cases used to estimate behavior in a larger population.
Confidence interval: a range that expresses uncertainty around an estimate, such as average quality or failure rate.
Variance: observed spread in outputs, scores, latency, cost, or behavior.
Rubric: a structured scoring guide that defines quality dimensions and score anchors.
LLM-as-a-judge: using a language model to evaluate outputs, usually with a rubric and examples.
Calibration: checking whether judge or rater scores align with trusted human judgment or known standards.
Slice: a segment of cases, users, languages, workflows, risks, or categories reported separately from the aggregate.
Golden set: a curated set of important examples used for regression and comparison.
RAG: retrieval-augmented generation, where retrieved documents are used as context for generation.
Groundedness: whether an answer is supported by the evidence or sources it was supposed to use.
Trajectory: the path an agent takes, including plans, tool calls, observations, state updates, and final answer.
Blocker: a hard failure that should stop release regardless of average score.
Canary: a limited production rollout used to observe behavior before wider release.
Data residency: where data is stored or processed geographically.
Cost per successful outcome: the total cost required to produce a result that meets quality and safety requirements.

A glossary earns its place when it prevents a meeting from using one familiar word to hide five different uncertainties.

## Expert Notes

In a real release review, treat the glossary as a living artifact. Update it when the organization invents new failure categories, metrics, release gates, or governance concepts.
