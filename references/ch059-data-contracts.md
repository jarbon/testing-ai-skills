# Section 59: Data Contracts for AI Systems

**Book location:** Chapter 8, Operating AI: Observability, Relevance, and Economics  
**Use when:** data contract, refusal, data contracts  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI systems need explicit contracts for what they receive, produce, cite, log, refuse, and do.

## Actions

- Start with input contracts.
- Define required fields, allowed formats, maximum sizes, language assumptions, privacy classifications, and what happens when data is missing or malformed.
- Define prompt contracts.
- Define tool-call contracts.
- Define output contracts.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for data contract, refusal, data contracts needed to reproduce work on Data Contracts for AI Systems.
- Report results for data contract, refusal, data contracts by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Data contracts define the shape and rules of AI system inputs and outputs. They make non-deterministic systems testable by specifying what must remain deterministic around the model.
For example, an agent may generate flexible language, but its tool call must follow a schema, its citation must reference a real source, its refusal must use an approved policy category, and its logs must not contain secrets.

Start with input contracts. Define required fields, allowed formats, maximum sizes, language assumptions, privacy classifications, and what happens when data is missing or malformed.
Define prompt contracts. What context is allowed into the prompt? What must be redacted? What policy sections must be present? What source metadata must travel with retrieved chunks?
Define tool-call contracts. Tool names, arguments, types, permissions, idempotency, confirmation requirements, and error behavior should be explicit.
Define output contracts. Structured outputs should validate against schemas. Free-text outputs should still obey constraints for citations, safety, tone, formatting, and required disclosures.
Define citation contracts. A citation should identify a source that exists, was available to the model, and supports the claim it is attached to.
Define refusal contracts. The system should know when to refuse, how to explain the refusal, and what safe alternative or escalation to offer.
Define logging contracts. Logs should capture enough for debugging and evaluation without storing secrets, private data, or unnecessary prompt content.
Contracts do not remove uncertainty from the model. They put stable rails around it so builders can find and explain failures.

## Context Engineering as a Test Surface

Context engineering is the work of deciding what the model sees. It includes prompt templates, system instructions, retrieved chunks, memory, user state, tool results, policies, examples, schemas, and ordering. For many AI products, context engineering matters as much as model choice.

Test the context as an artifact. Verify which fields enter the prompt, which fields are redacted, which sources are trusted, which sources are merely evidence, and which sources are untrusted user or web content. Check ordering effects: a safety policy buried after a long transcript may not behave like the same policy placed before the transcript. Check truncation effects: the most important source can silently fall out of the context window.

The best context tests save both the assembled prompt and the structured parts that created it. A trace should show the template version, section headers, variable values, retrieved chunks, memory entries, tool outputs, token counts, omitted material, and the rule that decided what to include. If a model gives a bad answer, the first question is often not "why did the model think that?" It is "what did we show it?"

## Structured Outputs and Parser Contracts

Structured outputs make AI systems easier to integrate, but they do not make them correct. A JSON response can validate against a schema and still contain the wrong customer ID, unsupported citation, unsafe tool argument, or misleading confidence score.

Test structured output in layers:

- schema validity: required fields, enums, types, arrays, nesting, and size limits
- semantic validity: field values mean what downstream systems think they mean
- safety validity: no secrets, hidden instructions, unsafe HTML, or unauthorized actions
- parser behavior: malformed JSON, partial output, duplicate keys, extra fields, encoding issues, and repair attempts
- downstream behavior: what happens when a valid-looking object triggers a tool call, refund, email, code change, or robot action

Treat repair logic carefully. A parser that "fixes" malformed model output can hide quality problems or create new ones. The release report should say how often structured outputs required repair, which fields were repaired, and whether repaired outputs are allowed to trigger side effects.

## Case Study: Mars Climate Orbiter

In 1999, NASA lost the Mars Climate Orbiter because two parts of the system disagreed about units. One team produced thruster data in pound-force seconds. Another expected newton-seconds. The spacecraft did not fail because nobody could do math. It failed because the contract between systems was wrong.

That is the AI lesson. Most AI failures will not announce themselves as "the model is bad." They will look like a tool result with the wrong unit, a retrieval document with the wrong timestamp, a score with the wrong scale, a user profile from the wrong account, a policy file from the wrong version, or a JSON field that technically exists but means something different than the caller assumes.

A data contract is not paperwork. It is a shared promise about meaning. For AI systems, every prompt, tool call, retrieval result, judge score, citation, model output, memory entry, trace, and release metric should carry enough context to be interpreted correctly: schema, units, source, timestamp, version, permissions, confidence, and allowed use.

The Mars Climate Orbiter lesson is blunt: a system can be full of smart people, expensive engineering, and individually working components, and still fail because the boundary between components lied. AI systems create more of those boundaries, not fewer.

Source: [NASA, Mars Climate Orbiter Mishap Investigation Board report](https://ntrs.nasa.gov/citations/20060043364)

## From the Field: The Empty Prompt That Talked Back

When one of the first LLM APIs was released, I did what every tester does eventually: I sent the weirdest boring input I could think of. In this case, I passed an empty string as the prompt.

The expected contract seemed obvious. Maybe the API should return nothing. Maybe it should return a validation error. Maybe it should say the prompt is required. What came back instead, in those early days, looked like somebody else's prompt. I did not know whether it was training data, generated text, test prompts, or real user input. That uncertainty was the problem.

Because there was even a chance that private information or user prompts were leaking, I reported it. At first, the response was quick enough that I thought the issue was being taken seriously. Then things got quiet. When I eventually heard more, the answer was basically that this was expected behavior for an LLM. I pushed back. If an empty prompt can produce text that looks like another user's prompt, the quality question is not only whether the model is "working as designed." The quality question is whether the API contract, privacy boundary, and incident response are good enough for real users.

Maybe it really was random generated text. Maybe it was only training data. Maybe no live user prompt was ever exposed. But from the outside, the perception was that user PII or user prompts might be leaking. For an early-stage technology surrounded by privacy, data-rights, and trust questions, that perception should have been treated as high priority. Quality is not only the internal truth of the system. It is also whether users can reasonably trust how the team responds when something looks unsafe.

And yes, because I am me, I wrote a small loop and sampled a lot of these empty-prompt responses. They were not all the same. Many did not look like generic training examples. I did not publish them, but the lesson stuck: test the exposed API surface, not only the friendly product workflow. Send empty strings, missing fields, nulls, oversized inputs, strange encodings, and prompts that should never produce private-looking output. If anything even smells like PII, treat it as a serious incident until proven otherwise.

The practical contract is simple: missing input should have a boring, deterministic, privacy-safe response. It should not improvise.

## Expert Notes

In production work, AI data contracts should be machine-validated, versioned, attached to traces, enforced at runtime, and tested with malformed inputs, adversarial prompts, missing fields, tool errors, and policy changes.
