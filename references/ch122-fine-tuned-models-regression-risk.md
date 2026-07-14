# Section 122: Fine-Tuned Models and Regression Risk

**Book location:** Chapter 15, How Models Work  
**Use when:** fine-tuning, fine tuned models regression risk  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A fine-tune can improve one behavior while quietly damaging another. Validate the whole model,
not only the task you tuned for.

## Actions

- Validate the whole model, not only the task you tuned for.
- Track before-and-after scores for the target task and for important safety, reliability, policy, language, and edge-case slices.
- Treat a small target gain with a large hidden regression as a failed release candidate.
- Watch especially for overfitting to the eval.
- Do not fine-tune if the data is noisy, the policy is still changing, the eval is weak, the labels reflect conflicting opinions, or the failure comes from missing evidence rather than model behavior.

## Evidence to Produce

- Track before-and-after scores for the target task and for important safety, reliability, policy, language, and edge-case slices.
- Include rare cases, adversarial cases, minority-language cases, safety boundaries, and examples where the teacher was known to be wrong.
- Report target-task improvement, regression slices, severe failures, confidence intervals, and category-level churn.
- Preserve the inputs, versions, configurations, raw outcomes, and results for fine-tuning, fine tuned models regression risk needed to reproduce work on Fine-Tuned Models and Regression Risk.

## Chapter Guidance

## Gentle Math Introduction

Think of fine-tuning as nudging a model's behavior distribution. You are not changing one isolated function. You are changing probabilities across many possible answers, refusals, formats, tool calls, and reasoning paths.

That means the validation question is not only, "Did the fine-tuned model improve on the target task?" The better question is, "Did the target task improve enough to justify any regressions elsewhere?"

The math can stay simple at first. Track before-and-after scores for the target task and for important safety, reliability, policy, language, and edge-case slices. Put confidence intervals around the changes. Treat a small target gain with a large hidden regression as a failed release candidate.

## Overview

Fine-tuning adapts a model to a domain, product voice, output format, tool workflow, label taxonomy, or specialized task. It can be useful when prompting alone is not enough, when a model needs to follow a stable style or schema, or when a smaller model needs to perform a narrow task cheaply.

But fine-tuning can also create regressions. A customer-support fine-tune may improve empathy while weakening policy refusals. A coding-agent fine-tune may match repository style while adding insecure patterns. A medical-imaging fine-tune may improve one hospital's scanner distribution while hurting another site's images. A robot-policy fine-tune may improve warehouse pick-and-place but reduce safety margins in homes.

This is why fine-tuned models need both a target-task eval and a broad regression suite. The target-task eval asks whether the fine-tune accomplished its intended purpose. The regression suite asks what else changed.

Good validation separates training data, validation data, and final holdout data. The holdout set should include examples the fine-tune never saw, examples from outside the target distribution, and cases that are important even if they are rare. If the fine-tune was trained from human labels or AI-generated labels, test label quality and labeler bias as part of the model behavior.

Watch especially for overfitting to the eval. A fine-tuned model can learn the labeler's style, the rubric wording, the examples in the training set, or the shape of the benchmark without becoming more generally useful. If the system looks better only where the training data was dense, you may have tuned the model to the measurement instrument rather than to the real product.

## Before You Fine-Tune

Fine-tuning should be a deliberate choice, not the first reflex after a bad output. Before changing weights, ask whether a smaller change would solve the problem with less regression risk.

Try the boring fixes first:

- Improve the prompt or rubric.
- Add missing context through retrieval.
- Fix stale or low-quality source documents.
- Add structured output constraints.
- Add deterministic validators or policy checks.
- Route hard cases to a stronger model or a human.
- Narrow the product workflow so the model has less ambiguous work to do.

Fine-tune when the behavior is stable, repeated, important, and hard to fix from the outside. Good reasons include a stable output format, a specialized label taxonomy, domain language the base model consistently misses, a narrow routing or classification job, or a need to make a smaller model perform a specific task cheaply.

Do not fine-tune if the data is noisy, the policy is still changing, the eval is weak, the labels reflect conflicting opinions, or the failure comes from missing evidence rather than model behavior. A fine-tune trained on confused feedback usually produces a more confidently confused model.

## Distillation and Teacher-Model Risk

Distillation uses a stronger or larger model to help train, label, or shape a smaller model. It can reduce cost and latency, create a private local model, or turn an expensive judge into a cheaper production classifier.

The risk is that the student inherits the teacher's mistakes. If the teacher hallucinates, over-refuses, under-refuses, misses a cultural context, or scores bugs according to a weak rubric, the distilled model can learn that behavior at scale. Distillation can also erase rare capabilities: the student may perform well on common cases while losing the edge cases the bigger model handled.

Test distillation like any other training pipeline. Keep human-reviewed holdouts. Include rare cases, adversarial cases, minority-language cases, safety boundaries, and examples where the teacher was known to be wrong. Compare the student not only against the teacher's labels, but against independent evidence. A smaller model that agrees with the teacher is not automatically correct.

## Expert Notes

In production work, treat a fine-tune as a model change with broad behavioral blast radius. Keep a locked holdout set that the tuning process never sees. Compare base and fine-tuned models with paired cases when possible. Report target-task improvement, regression slices, severe failures, confidence intervals, and category-level churn.

Useful techniques include before-and-after evals, paired comparisons, slice confidence intervals, chi-squared checks for category distributions, McNemar-style paired flip checks for binary outcomes, calibration curves, red-team suites, safety evals, multilingual slices, and production shadow testing. McNemar's test is useful when the same cases are run through two versions and each case has a binary result, such as pass/fail, safe/unsafe, grounded/hallucinated, or escalated/not escalated. Instead of asking only "what was the new failure rate?", it asks a sharper question: among the cases that changed, did far more cases flip from bad to good than from good to bad? That is the signal you care about when a fine-tune claims to reduce failures without creating an equally worrying new failure pattern.

Treat fine-tuning as one possible fix, not the automatic one. Sometimes retrieval, prompting, tool constraints, model routing, structured outputs, adapters, or product workflow changes solve the problem with less regression risk. When you do fine-tune, document the base model, data source, label process, labeler population, tuning method, hyperparameters, intended use, excluded use, evaluation suite, and rollback plan.
