# Testing AI Skill

An actionable companion to [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1).

This repository installs **one registered skill**. Its `SKILL.md` contains the decision workflow and a chapter-specific routing catalog. The 194 chapter references and 23 theme references live under `references/` and are loaded only when relevant. That progressive-disclosure design avoids trigger collisions and keeps the standing context small.

## Install

Install this repository as a Codex skill, or copy it into your local skills directory as `testing-ai-book`.

## Use

Ask the agent to use `$testing-ai-book` for an AI quality task, such as:

- Compare two prompt or model versions and decide whether the measured improvement supports release.
- Evaluate a RAG system for retrieval quality, groundedness, and citation faithfulness.
- Design an eval for a tool-using agent, including trajectory evidence and permission boundaries.
- Review AI-generated code for functional, security, privacy, integration, and maintainability risk.
- Produce an evidence-backed ship, canary, hold, rollback, or collect-more-evidence recommendation.

The skill instructs the agent to inspect or run available artifacts, preserve reproducible evidence, challenge the measurement system, and lead with a concrete decision rather than a generic test plan.

## Structure

- `SKILL.md`: registered workflow and routing catalog
- `agents/openai.yaml`: skill display metadata and default invocation
- `references/chNNN-*.md`: actionable chapter guidance loaded on demand
- `references/theme-*.md`: cross-section routes and evidence checklists

Book: https://www.amazon.com/dp/B0H8J9GCK1
