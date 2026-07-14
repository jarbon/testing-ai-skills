# Section 130: Activation and Concept Probes

**Book location:** Chapter 16, Introspection: White-Box Testing Networks  
**Use when:** activation, concept probe, activation concept probes  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Activation and feature probes are emerging comparison tools, not validated meters for meaning,
safety, or correctness.

## Actions

- Compare the same curated case across a model swap or fine-tune, and compare nearby cases that differ in one controlled way.
- Validate the relationship on held-out positive, negative, ambiguous, and adversarial cases.
- Then test whether an intervention such as activation patching changes behavior in the predicted direction.
- Treat a neuron as a probe whose precision and recall must be measured, not as a literal cell containing the concept.
- Measure feature purity, false activations, missed activations, sparsity, stability across prompts and languages, and drift across checkpoints.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for activation, concept probe, activation concept probes needed to reproduce work on Activation and Concept Probes.
- Report results for activation, concept probe, activation concept probes by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

Attention describes relationships among positions. Activation diagnostics ask a different question: which internal signals changed as the model processed a case? Teams can compare hidden-state, attention-block, or multilayer perceptron (MLP) output magnitudes across layers; train probes against labeled concepts; use activation or attribution patching; inspect candidate features; or use sparse autoencoders to separate patterns that raw neurons mix together. These methods measure different things and should not be collapsed into one generic "interpretability score."


Figure 16-6 is a real trace, not an illustrative concept curve. The x-axis is decoder layer. The y-axis is the mean L2 norm of the captured MLP output vector over the selected token span. The blue line uses the literal prompt token span "AI," and the green line uses "Testing." A larger value means a larger vector magnitude at that location; it does not mean the model assigned a higher probability, confidence, importance, or semantic strength to the concept.

An output-norm profile can spike, fade, persist, or reappear across decoder layers. The shape is usually more useful than a dramatic individual number, but magnitude alone omits activation direction and which features contributed to it. Compare the same curated case across a model swap or fine-tune, and compare nearby cases that differ in one controlled way. Large, reproducible changes can tell the team where to replay behavioral evals, inspect prompts, or add expert review.

## From Activations to Concepts

A signal profile can compare measurements from residual-stream, attention-block, and MLP pathways. Figure 16-7 uses the same real token-span trace as Figure 16-6, but independently scales every token-span and signal series from 0 to 1. That makes profile shapes easier to compare while deliberately discarding their incompatible raw magnitudes.


The three panels do not show probabilities or calibrated concept scores. "MLP output norm" is the magnitude of the captured MLP output. "Attention output norm" is the magnitude of the attention block's output vector, not an attention weight. "Residual-stream norm" is the hidden-state magnitude carried through the residual stream. Because every series is normalized independently, a value of 1 means only "the maximum observed value in this series." It does not mean that two pathways reached the same absolute magnitude or semantic importance.

A useful internal pattern is one that repeatedly predicts real behavioral differences across many cases, not one that simply looks intuitive. Validate the relationship on held-out positive, negative, ambiguous, and adversarial cases. Then test whether an intervention such as activation patching changes behavior in the predicted direction. Similar outputs may arise from different internal profiles, and similar profiles may produce different outputs.

Candidate concept neurons are even easier to overstate. A neuron that responds to credential examples may also respond to unrelated syntax or training patterns. Neural representations are often polysemantic: one unit participates in several features, and one feature is distributed across many units. Treat a neuron as a probe whose precision and recall must be measured, not as a literal cell containing the concept.

Sparse autoencoders attempt to recover cleaner features from entangled activations. They can make internal patterns easier to inspect, but they add another learned measurement system with its own training data, thresholds, omissions, and instability. Feature visualization, hidden-state probes, activation patching, and attribution patching provide additional evidence about where a behavior may be represented or causally influenced. None of them removes the need for behavioral evaluation.

### Raw Neurons and SAE Features

The fastest way to understand the motivation is to inspect top-activating examples. The following examples are deliberately illustrative, not measurements from the earlier model trace:

| Representation | Illustrative top-activating examples | What an investigator might conclude |
| --- | --- | --- |
| Raw neuron N817 | `dog`, `refund`, `JavaScript`, `ocean`, `invoice` | The neuron responds across unrelated domains. It is a polysemantic candidate, not an "animal neuron" or "refund neuron." |
| SAE feature F302 | `dog`, `cat`, `wolf`, `fox`, `fur` | The examples form a more coherent animal-related cluster. "Animal" is still a tentative human label that must be tested. |
| SAE feature F711 | `refund`, `invoice`, `chargeback`, `receipt`, `payment` | The feature may track financial disputes or transactions, but nearby negative examples are needed to define its boundary. |
| SAE feature F128 | `JavaScript`, `compiler`, `stack trace`, `JSON`, `CUDA` | The feature appears software-related, although it may still combine several technical subtopics. |

An SAE does not literally cut neuron N817 into three named pieces. It learns a new sparse feature basis from patterns distributed across many raw activations. One raw neuron can contribute to several learned features, and one learned feature can depend on many neurons. Humans or automated methods inspect the top-activating examples and assign provisional labels afterward.

A clean-looking list is only the beginning. Measure feature purity, false activations, missed activations, sparsity, stability across prompts and languages, and drift across checkpoints. Then test whether the feature predicts behavior or supports a successful intervention. Otherwise the SAE has produced a compelling label, not dependable quality evidence.

## Validate the Probe

**Before using an activation or concept probe operationally, test it like any other classifier.**

- define positive, negative, ambiguous, and adversarial cases;
- measure false positives, false negatives, stability, and slice behavior;
- compare model versions without silently changing the probe or aggregation;
- test whether interventions on the suspected feature change behavior in the predicted direction;
- keep output quality, traces, and expert review in the decision.

The strongest practical use today is comparative triage. If a candidate model passes the same output cases but its uncertainty or safety-related probe distribution moves well outside the historical band, investigate. That drift does not prove the candidate is worse. It identifies a claim worth testing with stronger behavioral or causal evidence.
