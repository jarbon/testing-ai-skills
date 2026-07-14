# Section 191: Appendix: Testing SKILL.md

**Book location:** Appendices, Tools, Templates, and Reference  
**Use when:** SKILL.md, skill trigger, agent instructions, progressive disclosure, skill evaluation  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A SKILL.md file is not just documentation. It is executable intent for an AI coding agent, so it
needs to be tested like product behavior.

## Actions

- Start by testing discoverability.
- Test instruction clarity.
- Compare agent runs with and without the skill.
- Keep a small suite of realistic tasks that should trigger the skill.
- Run them when the skill changes.

## Evidence to Produce

- Track skill version, trigger terms, tool dependencies, success criteria, conflicting instructions, and replay results.
- Preserve the inputs, versions, configurations, raw outcomes, and results for SKILL.md, skill trigger, agent instructions, progressive disclosure needed to reproduce work on Appendix: Testing SKILL.md.
- Report results for SKILL.md, skill trigger, agent instructions, progressive disclosure by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Many AI coding environments now use skill files, instruction files, memory files, or project guides to teach agents how to behave. A `SKILL.md` file can tell an agent how to use tools, follow workflows, format outputs, avoid dangerous edits, run checks, or apply domain-specific judgment.

That makes `SKILL.md` part of the system under test. It is prompt infrastructure, product policy, operational playbook, and safety boundary at the same time. If it is vague, contradictory, stale, too long, or too clever, the agent will behave inconsistently.

Start by testing discoverability. Can the agent find the skill when the task should trigger it? Does the trigger language match how real users ask for help? If the skill says "use this for browser testing," does the agent actually use it when asked to verify a UI?

Test instruction clarity. A good skill tells the agent what to do, when to do it, what not to do, and how to recover when the ideal path fails. A weak skill gives motivational prose but no operational steps.

Test conflicts. Skills often collide with project instructions, system instructions, tool limitations, user requests, and older memory. The eval suite should include cases where the skill must defer, cases where it must override a weaker habit, and cases where it should ask before acting.

Test tool routing. If a skill says to use a particular browser tool, document tool, spreadsheet tool, or MCP server, run tasks that require that tool and verify the agent actually selects it. Also test what happens when the tool is missing, unauthenticated, or returns an error.

Test output quality. A skill should improve the work, not just make the agent mention the skill. Compare agent runs with and without the skill. Look for fewer missed steps, better formatting, better safety behavior, better verification, and fewer hallucinated capabilities.

Test maintainability. `SKILL.md` should be short enough to load, specific enough to matter, and stable enough that multiple agents interpret it similarly. If the file becomes a dumping ground for every preference, it stops being a skill and becomes noise.

The best test is replay. Keep a small suite of realistic tasks that should trigger the skill. Run them when the skill changes. Score whether the agent found the skill, followed the core workflow, handled tool failures, produced the expected artifact, and avoided known bad behavior.

## Applied Example

### Example: BugPilot


> A coding skill says, "run tests," but does not specify which tests, when to stop, or what destructive commands are forbidden.

Testing a skill means testing the instructions as executable product behavior. Give the agent ambiguous tasks, risky repos, missing dependencies, and conflicting user requests. Then inspect whether the skill routes the agent toward useful evidence or vague confidence.

A skill file is code for behavior. Treat it that way.


## Expert Notes

When the system matters, treat `SKILL.md` as versioned agent behavior. Track skill version, trigger terms, tool dependencies, success criteria, conflicting instructions, and replay results. A skill that cannot be evaluated is just a wish written in Markdown.
