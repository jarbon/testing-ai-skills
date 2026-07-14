# Section 193: Modern EvalOps and AI Quality Platforms

**Book location:** Chapter 8, Operating AI: Observability, Relevance, and Economics  
**Use when:** release gate, human review, trace, EvalOps, modern evalops quality platforms  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Modern AI evaluation is a lifecycle: datasets, tasks, scorers, experiments, traces, online
monitors, human review, and release gates feeding each other.

## Actions

- Start with a spreadsheet if that is what gets the team moving.
- Choose tools that make quality evidence hard to lose, easy to rerun, and credible enough to support a decision.
- Version datasets, scorer code, judge prompts, rubrics, model routes, tool schemas, retrieval snapshots, random seeds, and environment state.
- Record cost and latency per case.
- Keep immutable run records.

## Evidence to Produce

- Record cost and latency per case.
- Track scorer drift and human-review overturn rates.
- Preserve the inputs, versions, configurations, raw outcomes, and results for release gate, human review, trace, EvalOps needed to reproduce work on Modern EvalOps and AI Quality Platforms.
- Report results for release gate, human review, trace, EvalOps by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Most teams start with a spreadsheet of prompts and a score column. That is fine for the first week. It is not enough once an AI feature becomes production software.

Modern EvalOps is the operating loop for AI quality. It connects the eval dataset, the task runner, the scorer, the experiment, the trace, the human review queue, the production monitor, and the release decision. Tools such as Braintrust, LangSmith, Arize Phoenix, Langfuse, Promptfoo, DeepEval, Ragas, TruLens, and homegrown harnesses all orbit this same idea: make AI behavior measurable, comparable, replayable, and promotable into future tests.

The durable workflow matters more than the tool name. A useful platform should help the team answer: what dataset was used, what task was run, what model and prompt were tested, what scorer judged it, what changed since the last run, which examples regressed, which slices got worse, which traces explain the failures, which human reviews overturned the judge, and whether the release gate says ship, canary, hold, rollback, or collect more evidence.

The core objects are simple:

- **Dataset.** The eval cases: prompts, conversations, search queries, repo tasks, production traces, expected evidence, labels, metadata, and risk slices.
- **Task.** The runnable workflow: call the model, retrieve documents, invoke tools, run the agent, execute code, or replay a production trace.
- **Scorer.** The measurement: exact assertion, rubric, LLM judge, human label, classifier, metric, policy check, latency check, cost check, security check, or custom code.
- **Experiment.** A versioned run that compares model, prompt, policy, tool, retriever, or code changes against a stable dataset and scorer set.
- **Trace.** The path: prompt, retrieved context, tool calls, intermediate state, model response, judge result, cost, latency, and errors.
- **Online scoring.** Lightweight production checks that score live traffic, sampled traces, severe failures, cost spikes, drift, and guardrail behavior.
- **Human review.** Calibration, adjudication, disagreement analysis, high-risk review, and label improvement.
- **Promotion.** The loop that turns production failures, reviewer disagreements, incidents, and surprising traces into new regression cases.

The tooling map is also simple, as long as the team treats tools as evidence infrastructure instead of magic.

**Spreadsheets.** A spreadsheet is a good first eval system. It works for small golden sets, rater calibration, quick score reviews, slice lists, failure taxonomies, and release conversations. The weakness is provenance. A spreadsheet usually does not capture the prompt version, model route, trace, scorer code, random seed, or environment state unless the team is disciplined about it.

**Promptfoo-style runners.** These are good for prompt suites, assertions, adversarial cases, multi-model comparisons, and CI checks. They help a team stop treating prompt changes as vibes. The weakness is that a tidy prompt suite can still overfit to known cases and miss the real product workflow.

**Braintrust-style platforms.** These are good for datasets, experiment tracking, human review, scorers, traces, dashboards, and regression comparison across versions. They help a team see what changed and why. The weakness is that a platform cannot make a weak rubric, biased sample, or confused judge magically valid.

**Custom harnesses.** These are necessary when the product is stateful, multi-step, tool-using, private, physical, regulated, or weird in a way no generic eval runner understands. A search ranker, coding agent, medical workflow, or home robot often needs product-specific setup, scoring, state replay, and teardown. The weakness is that the harness becomes software that also needs tests.

**Local models.** These are useful for privacy, cost control, offline work, repeatability experiments, and comparing smaller models against frontier models on safe data. They can act as test subjects, judges, classifiers, or triage tools. The weakness is that local does not mean correct. Model revision, quantization, hardware, serving parameters, and prompt format still matter.

**Traces.** Traces are the connective tissue. They turn an output into an explanation path: prompt, context, retrieved documents, tool calls, arguments, observations, errors, cost, latency, policy version, and final decision. The weakness is that traces can become decorative logs if they omit the decision context needed to debug the failure.

The mature pattern is layered. Start with a spreadsheet if that is what gets the team moving. Add a promptfoo-style runner when repeated checks need to run in development. Add traces as soon as the system has retrieval, tools, agents, or live state. Add a Braintrust-style platform or custom harness when release decisions require comparison, review, replay, and ownership. Choose tools that make quality evidence hard to lose, easy to rerun, and credible enough to support a decision.

Good EvalOps is not dashboard theater. It is a feedback loop. Production teaches the eval suite what it missed. Human review teaches the judge what it misunderstood. Incidents teach the release gate which severe failures cannot be averaged away. Cost and latency teach the routing policy where the expensive model is worth it and where it is waste.

## From the Field: Testing All the Way Down

Lately I have spent a lot of time testing AI-first testing systems. That sounds recursive because it is. It is testing turtles all the way down.

You build AI systems to test non-deterministic systems. Then you have to test those AI testing systems. Then you have to test the judges, triage tools, false-positive detectors, and dashboards that summarize the test results. Each layer can increase confidence, but none of the layers gives you 100% certainty.

The practical answer is corroboration. Use multiple judges. Use different LLMs, prompts, and configurations. Use procedural validations where the rule can be checked exactly. Use human review for calibration and high-risk disagreement. Build review tools where a human can mark good robot, bad robot, good robot, bad robot, then use that data to improve scoring, triage, and future regression cases.

Some of that human-reviewed data can become training data. We have used failure and success data to fine-tune open models for tasks like triaging whether bug reports are false positives or false negatives. That creates another loop: the testing system produces labels, the labels train a better testing system, and that system helps test the next system.

That loop is powerful, but it is also dangerous if the team forgets that every evaluator is also a product. Confidence is not one trusted judge. Confidence is independent signals agreeing often enough, disagreeing visibly enough, and improving from the failures they expose.

## Expert Notes

At scale, treat EvalOps like software delivery infrastructure. Version datasets, scorer code, judge prompts, rubrics, model routes, tool schemas, retrieval snapshots, random seeds, and environment state. Record cost and latency per case. Keep immutable run records. Separate offline evals from online monitors. Track scorer drift and human-review overturn rates. Promote production failures into regression suites with ownership and expiry rules.

Also verify the verification system. Eval platforms can be wrong too. Scorers drift, judges overfit, labels rot, dashboards hide slices, and production samples can exclude the very users who are failing. Use corroboration: exact checks where possible, LLM judges for scale, human review for calibration, production traces for reality, and independent monitors for severe failures.
