# Section 33: Using Raters Well

**Book location:** Chapter 5, Judges, Humans, and Disagreement  
**Use when:** exact assertions, LLM judge, human rater, raters  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Human raters are not a checkbox. They are an evaluation instrument that needs selection,
calibration, workflow design, and quality control.

## Actions

- Use overlap deliberately.
- Keep raters blind when possible.
- Track disagreement as data.
- Track inter-rater agreement, rater-specific bias, calibration drift, fatigue effects, adjudication outcomes, and whether the rater population matches the user population.

## Evidence to Produce

- Track disagreement as data.
- Track inter-rater agreement, rater-specific bias, calibration drift, fatigue effects, adjudication outcomes, and whether the rater population matches the user population.
- Preserve the inputs, versions, configurations, raw outcomes, and results for exact assertions, LLM judge, human rater, raters needed to reproduce work on Using Raters Well.
- Report results for exact assertions, LLM judge, human rater, raters by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Raters help test non-deterministic systems when quality cannot be reduced to exact assertions. They can judge usefulness, tone, relevance, safety, policy fit, and whether an answer actually solves a user's problem.
For example, an LLM judge may score a support answer as complete, while an experienced support rater notices that it violates refund policy. A domain rater may also see that a technically correct answer would confuse a real customer.

The first decision is who should rate. Some tasks need ordinary users. Some need trained QA reviewers. Some need domain experts, policy experts, clinicians, lawyers, accessibility specialists, or native speakers. A cheap generic rater pool is not automatically wrong, but it must match the evaluation decision.
Raters need a rubric, anchor examples, and calibration rounds before their labels count. Calibration is where reviewers score the same examples, compare reasoning, resolve confusion, and sharpen the instructions.
Use overlap deliberately. Have multiple raters review the same item when the decision is important, ambiguous, high-risk, or being used to train a judge. Single-rater labels can work for low-risk, obvious cases, but they are fragile when quality is subjective.
Keep raters blind when possible. If a reviewer knows which output came from the new model, favorite vendor, or internal champion prompt, bias can creep in. Randomize output order and hide model identity for pairwise comparisons.
Track disagreement as data. Disagreement can mean the rubric is unclear, the task is ambiguous, the rater is undertrained, the item is genuinely subjective, or the system is producing borderline output.
Adjudication should be designed, not improvised. When raters disagree, decide whether a senior reviewer resolves the case, the item receives an uncertainty label, the rubric changes, or the example is excluded from a release gate.
Rater fatigue is real. Long labeling sessions, repetitive tasks, confusing guidelines, and emotionally heavy content reduce label quality. Quality checks should include attention checks, gold examples, time-on-task outliers, and drift over the session.
Raters are part of the evaluation system. Their selection, instructions, training, disagreement, and adjudication rules should be documented with the same seriousness as the model version and dataset version.

## Examples

### Example: TunedSearch


> "best treatment for runner's knee after marathon"

A general rater may reward a polished fitness blog. A physical therapist may prefer clinical guidance with caveats. A local user may care about nearby sports-medicine clinics. A medical-safety reviewer may penalize anything that overstates diagnosis.

Using raters well means matching rater expertise to the job:

- domain experts for medical or legal slices
- local raters for local intent
- native speakers for language and cultural nuance
- ordinary users for broad usability
- calibrated reviewers for policy boundaries

The rater pool becomes part of the product. If everyone labeling health queries is guessing from keywords, TunedSearch will learn that guessing.


## Expert Notes

At scale, treat raters as measurement instruments. Track inter-rater agreement, rater-specific bias, calibration drift, fatigue effects, adjudication outcomes, and whether the rater population matches the user population. If raters and users disagree systematically, the eval is measuring the wrong audience.
