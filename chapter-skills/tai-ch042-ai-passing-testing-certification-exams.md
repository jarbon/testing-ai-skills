---
name: tai-ch042-ai-passing-testing-certification-exams
description: 'Apply chapter 42 of Testing AI, AI Passing Testing Certification Exams, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to ai passing testing certification exams.'
---

# AI Passing Testing Certification Exams

Skill name: `tai-ch042-ai-passing-testing-certification-exams`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

When AI can pass certification-style testing exams, the human advantage moves from memorizing
terminology to designing evidence.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A recent study, *Can Language Models Pass Software Testing Certification Exams? a case study*,
asked whether language models can pass software testing certification exams using 30
International Software Testing Qualifications Board (ISTQB) sample exams across foundation,
advanced, specialist, and expert categories. The result was blunt: two models passed all 30
sample certification exams by scoring at least 65%. I will avoid commenting on whether 65%
should be considered "passing." That does not mean an AI officially became ISTQB certified. It
means certification-style exam questions are increasingly solvable by models, which should make
Confidence Engineers rethink what professional competence really means.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to treat certification performance as a benchmark with limits. The cited
ISTQB study used sample exams, not official proctored certification records. There is also a
contamination question: if sample questions, answer keys, explanations, or close variants were
public on the web, a model may have memorized some of the benchmark rather than learned testing
judgment.
