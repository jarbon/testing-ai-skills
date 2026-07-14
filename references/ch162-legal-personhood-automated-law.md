# Section 162: AI Legal Personhood and Automated Law

**Book location:** Chapter 19, Governance, Regulation, and Moral Futures  
**Use when:** legal personhood, legal personhood automated law  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

If AI systems become legal actors, then law becomes one of the most important AI quality
systems.

## Actions

- Treat future AI legal systems as executable governance.
- Define runnable checks that exercise legal personhood and legal personhood automated law.
- Set acceptable outcomes and blocker failures for legal personhood and legal personhood automated law before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for legal personhood, legal personhood automated law needed to reproduce work on AI Legal Personhood and Automated Law.
- Report results for legal personhood, legal personhood automated law by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Law has already learned to deal with non-human actors. Corporations are not people in the biological sense, but many legal systems treat them as [legal persons](https://en.wikipedia.org/wiki/Legal_person) for contracts, property, liability, speech, governance, and accountability. That does not mean corporations have human lives. It means law can create artificial actors because society needs a way to assign rights, duties, responsibility, and enforcement.

AI may eventually force a similar question. Not necessarily full human rights. Not necessarily anything close. But some future AI systems may become persistent enough, economically active enough, autonomous enough, or morally uncertain enough that law creates limited legal status for them. The European Parliament's [2017 robotics resolution](https://www.europarl.europa.eu/doceo/document/TA-8-2017-0051_EN.html) even discussed the possibility of "electronic persons" for some advanced autonomous systems, though that idea remains controversial and is not settled law.

For this book, the important point is not predicting the exact legal future. The important point is that once AI systems become legal actors, legal targets, legal agents, or rights-bearing entities, law and law enforcement become extensions of AI testing.

That sounds odd until you imagine the surface area. Automated systems may decide whether an AI agent can sign a contract, spend money, access compute, hold property, represent a user, receive notice, appeal a decision, be rate-limited, be shut down, or be treated as harmed. Those systems must be codified, automated, correct, reliable, auditable, appealable, and fair. In other words: they must be tested.

## Law as a Quality System

Legal systems already depend on rules, evidence, procedures, interpretation, enforcement, and appeals. AI makes those mechanics more explicit because machines need rules they can execute and logs they can inspect.

If a rule says an AI agent may negotiate a contract up to $10,000 but not bind a company above that amount, the enforcement system has to know which agent acted, under which authority, for which principal, in which jurisdiction, with which tool, with which counterparty, and with which approval. That is a trace.

If a rule says an AI system must be given notice before a model instance is suspended, deleted, or rate-limited, the system has to generate notice, record delivery, verify identity, track deadlines, handle appeals, and preserve evidence. That is a workflow under test.

If a rule says an AI cannot be used in certain contexts, or cannot target certain users, or cannot impersonate a human, the legal control becomes a guardrail. It needs samples, monitors, failure taxonomies, false-positive analysis, false-negative analysis, and rollback behavior.

## What to Test

Legal automation should be tested like safety-critical infrastructure, not like a settings page. Useful checks include:

- **Authority:** which AI system or human had legal authority to act, approve, delegate, appeal, or spend?
- **Identity:** was the AI, owner, operator, user, organization, and counterparty correctly identified?
- **Jurisdiction:** which law, policy, contract, or regulator applied to this action?
- **Notice:** did the affected party receive understandable notice at the right time?
- **Due process:** could a human or AI agent contest the decision, provide evidence, and receive review?
- **Evidence chain:** were prompts, policies, tool calls, model versions, data sources, decisions, and approvals preserved?
- **Enforcement correctness:** did the system enforce the rule it claimed to enforce?
- **Over-enforcement:** did it block lawful, useful, or protected behavior?
- **Under-enforcement:** did it allow unsafe, illegal, or unauthorized behavior?
- **Remedy:** when the system was wrong, could the harm be reversed, compensated, explained, or appealed?

## Running Examples

### Example: TunedSearch: The Appeal Was Rejected in Fourteen Milliseconds
> "File an appeal because my disability benefit was terminated after the system said I missed a medical review."

The user's AI assembles the records and files before the deadline. The agency's triage AI rejects the appeal fourteen milliseconds later because one document uses an old provider identifier. A notification bot sends the decision to an address the user changed last month, and the automated deadline service closes the case before a human sees it.

Each component followed a rule. The combined system denied any meaningful opportunity to understand, correct, or contest the decision.

Test the legal workflow end to end: identity, jurisdiction, evidence schemas, notice delivery, deadline calculation, reasons for decision, exception handling, human review, appeal, and preservation of the record. Inject stale addresses, conflicting dates, inaccessible documents, changed names, system outages, and rules that change while a case is open.

If law becomes executable at machine speed, due process must become an executable quality requirement too.

## Expert Notes

Treat future AI legal systems as executable governance. That means versioned laws and policies, machine-readable controls, formal schemas, audit logs, human review points, appeal workflows, legal hold, evidence retention, jurisdiction routing, and independent monitors.

The hard part is that legal systems are not pure code. They include interpretation, discretion, precedent, equity, intent, proportionality, and human values. Automating law does not remove judgment; it moves judgment into policy design, exception handling, escalation rules, and review boards.

If AIs someday receive limited legal rights or legal status, the testing problem gets stranger. The system may need to protect humans from AI, protect humans using AI, protect organizations from AI, protect society from AI, and maybe protect AI systems from careless humans. That is why legal automation must be transparent, contestable, and measured.

The future legal stack will need the same quality disciplines as the rest of this book: samples, slices, traces, rubrics, monitors, confidence, adversarial cases, severe-failure review, rollback, and continuous learning from production mistakes. Law will not be exempt from AI testing. Law may become one of its most important domains.
