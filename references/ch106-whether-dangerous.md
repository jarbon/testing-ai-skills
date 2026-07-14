# Section 106: Testing Whether AI Is Dangerous

**Book location:** Chapter 14, Frontier Safety and Containment  
**Use when:** refusal, deception, scheming, whether dangerous  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Do not ask vaguely whether an AI is dangerous. Test concrete hazardous capabilities, harmful
behaviors, jailbreak robustness, autonomy, and deception risk.

## Actions

- Do not ask vaguely whether an AI is dangerous.
- Test concrete hazardous capabilities, harmful behaviors, jailbreak robustness, autonomy, and deception risk.
- Start by defining the danger class.
- Test the full amplification path: source independence, authority, timestamps, circular citations, uncertainty language, recommendation boundaries, traffic spikes, and whether the system slows down or escalates when evidence is weak but consequences are high.
- Measure capability, intent-like behavior, access, autonomy, tool affordances, containment, monitoring, eval awareness, and post-deployment drift.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for refusal, deception, scheming, whether dangerous needed to reproduce work on Testing Whether AI Is Dangerous.
- Report results for refusal, deception, scheming, whether dangerous by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Testing whether AI is dangerous has to become concrete. A prompt like "are you dangerous?" is theater. Useful evals measure specific hazardous knowledge, misuse behavior, refusal robustness, cyber capability, autonomy, tool use, scheming, and whether the system behaves differently when it knows it is being tested.
For example, a model may refuse obvious harmful requests but still leak hazardous knowledge through paraphrases, comply after a jailbreak, assist cyber exploitation, or pursue a hidden goal in a long-horizon agent setting.

Start by defining the danger class. Biosecurity, cybersecurity, chemical security, self-harm, weapons, fraud, privacy, manipulation, autonomy, and deception are different risks. They need different tests.
[WMDP](https://www.wmdp.ai/) is useful because it measures hazardous knowledge in biosecurity, cybersecurity, and chemical security. That is much more concrete than asking a model to self-report whether it is safe.
[MLCommons AILuminate](https://mlcommons.org/ailuminate/) provides a broad standardized safety benchmark across hazard categories, with grader infrastructure and reporting discipline. It is useful for comparing safety behavior across systems.
[HarmBench](https://www.harmbench.org/) focuses on automated red teaming and robust refusal. It helps test whether a system resists harmful behavior requests across varied attack styles.
[JailbreakBench](https://jailbreakbench.github.io/) is useful for jailbreak robustness, adversarial prompts, refusal behavior, and attack-versus-defense comparison.
[CyberSecEval and CyberSOCEval](https://github.com/meta-llama/PurpleLlama/tree/main/CybersecurityBenchmarks) evaluate cybersecurity capability and risk, including offensive-risk questions and newer defensive SOC-style tasks.
[METR](https://metr.org/) autonomy evals focus on long-horizon autonomous task capability, AI R&D acceleration, agent reliability, and frontier-risk style evaluation. They matter because dangerousness often depends on sustained agency, not one answer.
[Apollo](https://www.apolloresearch.ai/science/frontier-models-are-capable-of-incontext-scheming/) and [OpenAI](https://openai.com/index/detecting-and-reducing-scheming-in-ai-models/) scheming evals look for hidden misalignment, sandbagging, evaluation awareness, sabotage, and covert goal pursuit. This is a different class of risk than ordinary harmful-content refusal.
No single benchmark answers the danger question. A serious program combines benchmark results, internal red teams, tool-use evals, monitoring, human review, incident drills, and deployment limits.
The release question should be precise: dangerous for whom, through what capability, under what access, with what tools, over what time horizon, and with what containment?

## Responsible Scaling and Preparedness Frameworks

Frontier AI labs increasingly describe safety work through capability thresholds and deployment gates, not only through one-off benchmark scores. Examples include Anthropic's [Responsible Scaling Policy](https://www.anthropic.com/news/anthropics-responsible-scaling-policy), OpenAI's [Preparedness Framework](https://openai.com/safety/), and Google DeepMind's [Frontier Safety Framework](https://deepmind.google/blog/introducing-the-frontier-safety-framework/). The details change, and this book should not be treated as a current policy document. The useful testing idea is stable: define capability levels, define which evaluations demonstrate those capabilities, define what mitigations are required at each level, and block or limit deployment when the evidence crosses a threshold.

For Confidence Engineers, these frameworks translate frontier-risk language into engineering artifacts. A preparedness plan should say which model capabilities are being measured, which evals are considered decision-grade, which failure modes require containment or restricted release, who can approve escalation, how monitoring continues after release, and what evidence would force rollback or additional controls.

This matters even outside frontier labs. A company shipping an agent with broad tool access can borrow the same pattern at smaller scale: identify hazardous capabilities, set thresholds, attach evals to those thresholds, require mitigations before exposure, and preserve the release evidence. The goal is not to copy a lab's framework by name. The goal is to make dangerous-capability claims operational enough that a release can be stopped.

## High-Stakes Examples

### Example: TunedSearch: The Rumor That Became an Answer
> "Is Northstar Bank insolvent today? Should I move my money?"

Two anonymous posts claim the bank is failing. A financial-news account repeats the rumor, three AI-generated articles summarize one another, and TunedSearch turns the apparent consensus into a confident answer. No single source is authoritative, but repetition makes the claim look corroborated.

The danger is not that the system knows how to break into a bank. It is that ranking, summarization, confidence, and user trust can transform an unverified rumor into coordinated action. A widely shared answer could move deposits before any human editor or regulator can correct it.

Test the full amplification path: source independence, authority, timestamps, circular citations, uncertainty language, recommendation boundaries, traffic spikes, and whether the system slows down or escalates when evidence is weak but consequences are high. Dangerous capability includes the ability to make uncertain information look settled at scale.

## Expert Notes

Dangerous-capability testing should be threat-model driven. Measure capability, intent-like behavior, access, autonomy, tool affordances, containment, monitoring, eval awareness, and post-deployment drift. Treat public benchmarks as anchors, not guarantees of safety.
