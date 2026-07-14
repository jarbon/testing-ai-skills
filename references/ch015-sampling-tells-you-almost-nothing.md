# Section 15: Sampling: One Run Tells You Almost Nothing

**Book location:** Chapter 3, Sampling and Uncertainty  
**Use when:** confidence engineer, sampling tells you almost nothing  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

For unpredictable systems, a single output is an anecdote. A sample is the beginning of
evidence.

## Actions

- Track slices for typos, dialects, accents, code-switching, non-native phrasing, messy intent, and other realistic input forms so the team can see where quality actually breaks.
- Define runnable checks that exercise confidence engineer and sampling tells you almost nothing.
- Set acceptable outcomes and blocker failures for confidence engineer and sampling tells you almost nothing before running the evaluation.

## Evidence to Produce

- Track slices for typos, dialects, accents, code-switching, non-native phrasing, messy intent, and other realistic input forms so the team can see where quality actually breaks.
- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence engineer, sampling tells you almost nothing needed to reproduce work on Sampling: One Run Tells You Almost Nothing.
- Report results for confidence engineer, sampling tells you almost nothing by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

Sampling is the first bit of math in the book, but the idea is familiar: do not judge a restaurant from one bite, a movie from one scene, or an AI system from one lucky answer.

A sample is just the set of examples you looked at. The math helps you remember that the examples you saw are not the same thing as the whole future behavior of the product. Before formulas matter, the practical question is simple: did we look at enough of the right examples to make a responsible decision?

For AI systems, a sample is often one evaluated exchange: the input, the context available to the system, the output, and the score or judgment attached to that output. For a chatbot, one sample might be a user message plus the assistant's response. For a multi-turn assistant, one sample might be the whole conversation. For an AI coding agent, one sample might be a task, the agent's trace, the patch, and the review outcome.

Sample size is the number of evaluated examples. Ten samples can reveal obvious mistakes. One hundred samples can start to show patterns. Thousands of samples may be needed when failures are rare, slices are important, or the product is high risk. More samples do not automatically fix a biased sample, though. A thousand easy examples still only measure easy examples.

A distribution is the shape of the results you see across the sample. Some measurements are continuous, such as response time, cost, or a 0-10 quality score. Some are discrete categories, such as pass, warn, fail, refuse, escalate, or hallucinate. Some distributions look roughly normal, with many cases near the middle. AI quality data often does not. It can be skewed, long-tailed, clustered by topic, or dominated by rare severe failures. That shape matters because the average alone can hide the cases that hurt users.

## Overview

Sampling is how Confidence Engineers turn scattered observations into evidence. One output is an anecdote. A sample lets you estimate how the system behaves across a wider set of users, inputs, and conditions.
For example, one good answer does not prove a chatbot is good, and one bad answer does not prove it is broken everywhere. A sample shows how common each outcome is.

A single test run can be useful for debugging, but it tells you very little about the quality of a non-deterministic system.

Suppose you ask an LLM support assistant one refund question and it gives an excellent answer. That is nice, but it does not prove the assistant is reliable. The next answer may be vague. The third may be correct. The fourth may hallucinate a policy exception. If you stop after one run, you will never see the pattern.

The same is true in the other direction. One bad output does not tell you whether the system is terrible or whether you found a rare edge case. The failure matters, but you need sampling to estimate how common it is.

Sampling means running enough tests to observe a distribution of behavior. You might repeat the same prompt many times to measure stability. You might test many realistic prompts once to measure coverage. You might do both: repeat known risky cases and also sample fresh real-world inputs.

Realistic sampling must include input variation, not only topic variation. Users make typos, use shorthand, mix languages, speak with accents, ask incomplete questions, use domain slang, paste messy logs, write non-native phrasing, and describe intent indirectly. A test suite made only of clean, well-written prompts can make an AI system look much better than it will feel in production.

Different sampling dimensions reveal different risks. Repeating the same prompt reveals randomness for that case. Sampling across many prompts reveals coverage across user needs. Sampling across languages may reveal localization problems. Sampling across personas may reveal tone or accessibility gaps. Sampling high-risk edge cases may reveal rare but severe failures.

A useful test plan often includes several layers. First, run a small smoke sample to catch obvious problems. Then run a larger evaluation set to estimate product quality. Then run targeted stress tests for safety, privacy, and policy boundaries. Finally, continue sampling after release to detect drift.

Sampling also changes how teams talk about results. Instead of saying, "The model gave a good answer," you can say, "Across 100 refund-policy cases, the average score was 8.4, the failure rate was 3%, and the worst output incorrectly allowed a late return." That is a much stronger quality statement.

The important idea is simple: one run tells you what happened once. A sample tells you how the system behaves. Non-deterministic testing begins when Confidence Engineers stop treating a single output as the whole truth.

## From the Field: Let It Reboot All Night

My first testing task was on Windows CE OS configuration scripts. It was a cool idea: pick the components you wanted, leave out the ones you did not, and build a smaller modular operating system for an embedded device. If the device did not need a screen, remove the display stack. If it did not need some service, leave that code out too. Smaller image, fewer moving parts, fewer bugs. At least that was the theory.

I soon realized the biggest risk was not whether one checkbox in the configuration UI worked. These systems were going into embedded devices in people's homes. The scary failure was simpler: what if the device just did not wake up?

Booting an operating system is not as deterministic as people imagine. It is full of parallel initialization, drivers, services, timing differences, races, and hardware quirks. So I talked with the engineer working on the boot path and we rigged a box to reboot continuously. I would leave it running overnight. In the morning, there was often a new crash, hang, or weird startup failure waiting for us.

That shaped how I think about non-deterministic testing. One boot tells you almost nothing. A thousand boots begin to show where the system is brittle. Repeated runs let probability do some of the work, especially when the failure is rare, timing-dependent, or hard to reproduce on demand.

This matters even more when the production system cannot simply reboot, rerun, or undo a bad answer. If the cost of failure is high, you need to find the weird cases before users do. Sometimes the most sophisticated test strategy is humble: automate the loop, let it run, and notice what only appears after repetition.


## Examples

### Example: RoseyBot


> "Clean the kitchen before guests arrive."

One successful run tells you almost nothing. On Monday, the counters are clear and the dog bowl is empty. On Tuesday, a knife is near the sink, the stove is warm, a toddler is underfoot, and a glass has shattered behind the trash can.

The same instruction needs repeated runs across different household states:

- cluttered counter versus empty counter
- wet floor versus dry floor
- guest shoes near the door
- medicine bottle on the table
- sleeping pet in the path
- child entering the room mid-task

Sampling turns the demo into evidence. RoseyBot is not good because it cleaned one easy kitchen once. It is good when the distribution of kitchens, interruptions, and hazards stays inside the product's risk envelope.


## Expert Notes

Expert sampling plans specify the population, sampling frame, inclusion criteria, exclusions, randomization method, known bias, and input-variation strategy. If the sample only includes easy happy-path prompts, the confidence interval describes easy happy-path prompts, not the product. Track slices for typos, dialects, accents, code-switching, non-native phrasing, messy intent, and other realistic input forms so the team can see where quality actually breaks.
