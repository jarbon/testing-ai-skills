# Section 135: Testing Deep Personalization

**Book location:** Chapter 17, Personalized and Dynamic AI Products  
**Use when:** personalization, deep personalization  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Personalized AI will not have one correct answer. It will have behavior that must be right for
this user, in this context, under these constraints.

## Actions

- Start by testing the personalization contract.
- Test counterfactual users.
- Measure personalization lift separately from safety.
- Use sampling by user segment.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for personalization, deep personalization needed to reproduce work on Testing Deep Personalization.
- Report results for personalization, deep personalization by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Deep personalization changes the testing problem because the system no longer behaves the same way for everyone. It adapts to memory, preferences, history, goals, risk level, device, language, accessibility needs, and sometimes emotional state.
For example, a health coach, coding assistant, sales assistant, or learning tutor may give different advice to two users with the same prompt because their histories and constraints are different. That can be valuable, but it creates a much larger quality surface.

Start by testing the personalization contract. What is the system allowed to remember? What is it allowed to infer? What must it ask before using? What must it forget? What should never be personalized?
Personalization should improve relevance without creating unfairness, manipulation, privacy leakage, or brittle user profiles. A system that becomes more useful by silently overfitting to a mistaken profile is not high quality.
Test counterfactual users. Hold the task constant and vary user profile attributes, accessibility needs, language, past behavior, risk category, and permissions. The differences should make sense and should not create protected-class harm.
Test profile drift. A user's needs change. A student learns, a customer changes plans, a patient updates symptoms, and an employee gets a new role. The AI should adapt without dragging old assumptions forever.
Test memory correction. Users need ways to inspect, correct, delete, and override remembered facts. A wrong memory can poison every future answer.
Measure personalization lift separately from safety. Better relevance is not an excuse for privacy failure, unsafe advice, or manipulative targeting.
Use sampling by user segment. Average quality can hide the fact that personalization helps power users while harming new users, multilingual users, disabled users, or users with sparse histories.
The best personalized AI feels context-aware without feeling invasive. Testing has to measure both usefulness and trust.

## From the Field: There Be Dragons

When I first got to Google, I was excited to see what search looked like behind the firewall. I had just come from Bing. During my first week or two of Noogler training, after getting through the paperwork, I skipped a lot of the classes and went straight over to the search building.

I wandered around the cubicles and offices asking what people worked on. The funny thing was that Google was huge, the campus was huge, but a surprising amount of the useful search work was concentrated in one building. I kept telling people I was new and that I wanted to work on search personalization.

The reaction was basically: lower your voice.

People warned me away from it. Several waves of smart people had tried to personalize web search before. Some ideas had failed. Some teams had moved on. Some people had left. Personalization sounded obviously powerful from the outside, but inside search it carried a reputation: dangerous, complicated, hard to measure, and politically risky.

The measurement problem was the real dragon. If you build a perfectly personalized search system for everyone on earth, you are no longer testing one search engine. You are testing billions of search engines. Even if you split only by simple demographics, location, language, device, history, and intent, the number of slices explodes. And because search is already non-deterministic, every slice still needs enough samples to know whether the change helped or hurt.

At the time, there was not enough compute in the world to measure personalization naively. You had to be creative. You had to find heuristics, proxy evals, clever holdouts, high-value slices, and ways to separate true personalization lift from noise, creepiness, bias, latency, and ordinary ranking churn. I eventually found a path and got a team together, but the warnings were not wrong.

Personalization is one of the most tempting roads in AI because the upside is huge: the system can become more useful for a specific person in a specific moment. It is also one of the easiest roads to get lost on. There be dragons.

## Expert Notes

At scale, deep personalization testing should combine counterfactual profile testing, privacy audits, memory provenance, user-segment sampling, preference-reversal tests, drift monitoring, consent checks, and calibration of when the system should ask instead of infer.
