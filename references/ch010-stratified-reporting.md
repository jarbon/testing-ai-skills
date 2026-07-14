# Section 10: Stratified Reporting

**Book location:** Chapter 2, From Tests to Release Evidence  
**Use when:** stratified reporting, RAG  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Overall averages can hide weak segments. Break results down by the categories that matter.

## Actions

- Define runnable checks that exercise stratified reporting and RAG.
- Set acceptable outcomes and blocker failures for stratified reporting and RAG before running the evaluation.
- Run representative cases for stratified reporting and RAG and preserve the failures that would change the decision.

## Evidence to Produce

- Report the case by slice: - legal or policy-sensitive query - local jurisdiction - renter intent - mobile result page - freshness-sensitive law - official-source requirement The eval should not only say TunedSearch scored 8.1 overall.
- Preserve the inputs, versions, configurations, raw outcomes, and results for stratified reporting, RAG needed to reproduce work on Stratified Reporting.
- Report results for stratified reporting, RAG by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Stratified reporting breaks results into meaningful categories so weak spots do not hide inside a good average. It shows where quality is strong and where risk clusters.
For example, an assistant may average 8.4 overall but score 6.1 on Spanish billing questions or 5.8 on account deletion cases.

One average can hide the most important quality problem.

Suppose an AI support assistant has an overall average score of 8.4. That sounds good. But the breakdown tells a different story: English support cases score 8.8, Spanish support cases score 6.9, billing cases score 8.6, and policy edge cases score 5.8.

The overall average was not false. It was incomplete.

Stratified reporting means breaking results into meaningful categories. Those categories might include language, persona, input type, product area, risk level, customer segment, prompt length, device type, geography, policy category, or new versus returning users.

The right categories depend on the product. For an LLM support assistant, language and policy category may matter. For a recommendation engine, product category and customer segment may matter. For a fraud model, geography and transaction type may matter. For an AI agent, action type and reversibility may matter.

Stratified reporting is important because non-deterministic systems often perform unevenly. A model may be excellent with short English prompts and weak with long multilingual prompts. A ranking system may work well for popular inventory and poorly for rare items. An agent may answer questions safely but behave poorly when allowed to take actions.

A good report starts with the overall result, then immediately shows the most important breakdowns. It might say: overall average score is 8.4 and failure rate is 3.2%, but policy edge cases average 5.8 with an 18% failure rate. Recommendation: do not ship until policy-boundary behavior improves.

This kind of reporting prevents teams from hiding behind a comfortable average. It also helps engineering teams focus. Instead of "quality is bad," the report says, "quality is good overall, but Spanish policy edge cases are failing." That is actionable.

For high-risk systems, category-specific gates may be necessary. The overall score may need to be at least 8.0, but billing, privacy, and policy categories may each need their own thresholds.

Users do not experience the average. They experience their segment, their language, their workflow, and their edge case. Stratified reporting makes those experiences visible.

## Examples

### Example: TunedSearch


> "can my landlord use AI cameras in the hallway seattle"

A single average score hides too much. The result may be good for broad privacy queries and bad for location-specific housing-law queries. It may be good in California and weak in Washington. It may be good for desktop users who read ten results and bad on mobile where only the first answer is visible.

Report the case by slice:

- legal or policy-sensitive query
- local jurisdiction
- renter intent
- mobile result page
- freshness-sensitive law
- official-source requirement

The eval should not only say TunedSearch scored 8.1 overall. It should say whether renter-rights, local-law, mobile, and freshness slices stayed healthy. Stratified reporting turns one comforting number into the shape of the product risk.


## Expert Notes

When the system matters, define strata before the evaluation and ensure each important stratum has enough samples to support a decision. Too many tiny categories create noisy numbers; too few categories hide actionable risk.
