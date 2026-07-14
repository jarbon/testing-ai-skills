# Section 53: Synthetic Test Data

**Book location:** Chapter 8, Operating AI: Observability, Relevance, and Economics  
**Use when:** RAG, synthetic data, counterfactual, synthetic test data  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Synthetic data can expand coverage, but it can also manufacture a false picture of reality.

## Actions

- Use synthetic data to fill coverage gaps, not to replace reality.
- Ask for examples across languages, literacy levels, devices, regions, risk categories, and malformed inputs.
- Review them for realism, expected-answer quality, policy correctness, and whether they actually test the intended risk.
- Treat synthetic data as a hypothesis generator, not a substitute for measured production behavior.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for RAG, synthetic data, counterfactual, synthetic test data needed to reproduce work on Synthetic Test Data.
- Report results for RAG, synthetic data, counterfactual, synthetic test data by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Synthetic test data is useful when real examples are rare, sensitive, expensive, or not yet available. It can create edge cases, adversarial prompts, privacy-safe HIPAA-like examples, counterfactual bias cases, and regression scenarios.

HIPAA is the U.S. Health Insurance Portability and Accountability Act. In practical product work, people usually invoke HIPAA when they mean protected health information: patient names, dates of birth, account numbers, diagnoses, prescriptions, lab results, visit notes, images, insurance details, and other data that can identify a person in a healthcare context. A healthcare-adjacent AI feature may need to handle the shape of that data without letting real patient records leak into prompts, logs, eval reports, screenshots, vendor systems, or demo decks.

That is where synthetic data can help. A medical-style summarization eval can use synthetic patient notes to test omission risk, conflicting facts, abbreviations, medication names, allergy handling, escalation behavior, and privacy controls without exposing real patient records. The test can include a believable note for "Maria Chen, 52, allergic to penicillin, taking warfarin, reporting dizziness after a medication change" while still being completely invented. The point is not to fake compliance. The point is to exercise the product behavior before real protected data is approved.

Synthetic data is also useful for counterfactual bias testing. A team can hold the task constant while changing one attribute at a time: name, pronoun, age, disability cue, zip code, accent marker, language, job history, or family status. If the support bot, search ranker, hiring assistant, or medical triage model changes its recommendation for no task-relevant reason, the synthetic pair has exposed a bias hypothesis worth deeper measurement.

Regression scenarios are another strong use. Once the team finds a production failure, it can create a synthetic version that preserves the failure mechanism without preserving the customer's private facts. That synthetic case can live in the release gate forever: same kind of policy conflict, same tool boundary, same missing context, same unsafe shortcut, but no real customer record attached.

Use synthetic data to fill coverage gaps, not to replace reality. It is excellent for rare failures, malformed inputs, long-tail combinations, and cases the team wants to test before launch.
Synthetic examples should be labeled by intent. Is this a boundary case, adversarial case, bias counterfactual, privacy case, tool-failure case, or ordinary representative case?
Generate counterfactual pairs carefully. If only the protected attribute changes, the expected behavior should usually remain the same. If other details change, the test may be measuring the wrong thing.
Privacy-safe synthetic data is valuable, but it must not be copied from real records with minor edits. De-identification and synthesis are different tasks.
Synthetic data can create synthetic bias. A model-generated eval set may overrepresent what the generator imagines users do and underrepresent how real users behave.
Diversity prompts help, but sampling and human review still matter. Ask for examples across languages, literacy levels, devices, regions, risk categories, and malformed inputs.
Synthetic test cases should be validated. Review them for realism, expected-answer quality, policy correctness, and whether they actually test the intended risk.
The best strategy combines synthetic coverage with production sampling. Synthetic data explores the map. Production data tells you where users actually walk.

### Example: CartCare Chatbot

> I am dissatisfied with my order and would like assistance resolving this issue.

That is a fake customer. Real customers do not all write like polite training examples. They are rushed, vague, angry, funny, typo-heavy, multilingual, distracted, or emotionally loaded. Some say, "where is my stuff??" Some paste screenshots. Some threaten chargebacks. Some ask three things at once. Some are wrong about what they ordered.

The test should verify that synthetic conversations do not make CartCare look better than it is:

- Include terse messages, typos, slang, code-switching, and incomplete facts.
- Include angry but legitimate customers, not just abusive edge cases.
- Include users who confuse order numbers, dates, items, addresses, or refund rules.
- Include customers who ask for help indirectly: "so I guess I'm just out $80?"
- Include realistic pressure: spoiled food, missing medication, party catering, delivery delays, screenshots, and public complaints.
- Compare synthetic chats with real production traces to see whether the fake set is too clean, too polite, or too easy.

The regression question is not whether CartCare performs well on beautifully behaved fake customers. It is whether the test data contains enough human messiness to predict what will happen when real shoppers show up.

## From the Field: The Joke That Trained Autocomplete

Here is one more source of bad synthetic data that is easy to underestimate: deliberately modified internal data.

That sounds nefarious, but sometimes the motive is not villainy. Sometimes teams are tired, buried in data, and trying to have a small laugh. The problem is that training systems do not know the difference between a harmless joke and a pattern they should learn.

At Bing, some synthetic training data was modified around extremely rare, almost improbable queries. The twist was that those rare queries were combined with the name of a particular product manager. The query pattern was not exactly G-rated, and it was repeated enough that the model learned the association.

When the next build went out, typing that person's very specific name into the search box could trigger autocomplete suggestions with all sorts of terrible associations. The product manager thought it was funny. I am not sure management ever knew. The synthetic data did not make it into the next autocomplete training run.

The lesson is not "never have fun." The lesson is that synthetic data is not fake once it trains a model. It becomes product behavior. Joke rows, placeholder rows, poisoned rows, adversarial rows, and "this will never happen" rows should be labeled, reviewed, isolated, and kept out of training paths unless the team really intends the model to learn from them.

## Expert Notes

Track synthetic-data provenance, generator model, prompt, seed, intended risk, reviewer approval, similarity to real data, and downstream failure discovery. Treat synthetic data as a hypothesis generator, not a substitute for measured production behavior.
