# Section 11: Rare Failure Hunting

**Book location:** Chapter 2, From Tests to Release Evidence  
**Use when:** rare failure, RAG, rare failure hunting  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Average quality can look excellent while rare catastrophic failures still make the system
unsafe.

## Actions

- Track the worst observed output, the number of critical failures, the percentage below a threshold, safety failure rate, privacy failure rate, and policy violation rate.
- Define runnable checks that exercise rare failure, RAG, and rare failure hunting.
- Set acceptable outcomes and blocker failures for rare failure, RAG, and rare failure hunting before running the evaluation.

## Evidence to Produce

- Track the worst observed output, the number of critical failures, the percentage below a threshold, safety failure rate, privacy failure rate, and policy violation rate.
- Include examples of the worst outputs in the report so decision-makers can see the risk directly.
- Preserve the inputs, versions, configurations, raw outcomes, and results for rare failure, RAG, rare failure hunting needed to reproduce work on Rare Failure Hunting.
- Report results for rare failure, RAG, rare failure hunting by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Rare failures matter when severity is high. A system that behaves well 99% of the time can still be unshippable if the remaining 1% includes privacy leaks, unsafe instructions, or irreversible actions.
For example, an AI agent that usually books the right trip but occasionally confirms without approval has a rare-failure problem, not a small average-quality problem.

Some failures are rare but unacceptable.

An AI system can produce excellent answers 99% of the time and still occasionally leak private data, hallucinate a dangerous instruction, approve an invalid refund, or violate a safety policy. If the failure is severe enough, the high average does not make the system shippable.

This is why builders need rare failure hunting.

Averages are not designed to protect against catastrophic tails. Imagine 99 outputs score 9 and one output scores 0. The average score is 8.91. That sounds excellent. But if the score of 0 represents a privacy leak or unsafe instruction, the release risk is still real.

Rare failures require different tactics. Larger random samples can help, but they are not enough by themselves. If a failure is very rare, random sampling may miss it. Targeted stress testing is necessary.

The sharper move is to look for markers, not only more examples. In biology, if you are looking for a rare signal in a river, you might test for traces of DNA instead of scooping random buckets forever. AI systems have markers too: unusual confidence drops, strange tool retries, missing citations, safety-classifier wobble, logprob cliffs, weak retrieval scores, judge disagreement, malformed Unicode, or tiny deviations in the part of the response that normally stays stable. Those markers do not prove a catastrophic failure happened, but they tell you where to look.

For LLM systems, rare failure hunting may include prompt injection attempts, jailbreak attempts, policy-boundary questions, requests involving private data, ambiguous instructions, malicious users, conflicting instructions, marker-triggered investigations, and multilingual edge cases. For AI agents, it should include irreversible actions, tool misuse, permission boundaries, and cases where the agent should ask for confirmation or escalate.

The metrics should also change. Average score is not enough. Track the worst observed output, the number of critical failures, the percentage below a threshold, safety failure rate, privacy failure rate, and policy violation rate. Include examples of the worst outputs in the report so decision-makers can see the risk directly.

Rare failure hunting also belongs after release. Some failures only appear under real traffic, real user creativity, or real abuse pressure. Production monitoring, complaint analysis, and sampled evaluations can reveal failures the lab missed.

The practical lesson: average quality tells you how the system usually behaves. Rare failure hunting tells you whether the system can be trusted when it does not.

## Examples

### Example: DropDoc


> A user photographs a blood drop on a cracked phone screen while the camera flash reflects off a kitchen counter.

Most runs may work on clean, centered, well-lit images. The rare failures hide in the ugly corners: glare that looks like a bright cell cluster, a screen crack that becomes a false line, a skin tone or lighting combination underrepresented in training, or a compression artifact that the model treats as evidence.

Rare-failure hunting should deliberately search for those corners:

- old phones and cracked screens
- low light, flash glare, and motion blur
- unusual backgrounds
- tiny blood drops near the image edge
- users who retake the photo after wiping the lens
- medical-looking artifacts that are only camera artifacts

The release question is not, "Did DropDoc pass the normal photo set?" It is, "Have we gone looking for the weird photo that will create a confident wrong health signal?"


## Expert Notes

Expert rare-failure work treats zero observed failures carefully. If you test 100 cases and see zero failures, you have evidence, not proof. The upper bound on the plausible failure rate may still be too high for safety-critical behavior.
