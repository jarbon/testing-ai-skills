# Section 157: Ethics as a Test Surface

**Book location:** Chapter 19, Governance, Regulation, and Moral Futures  
**Use when:** release gate, trace, RAG, ethics, ethics test surface  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Ethics is not a poster on the wall. If an ethical claim matters, it should become evidence.

## Actions

- Score not only relevance, but source authority, freshness, sponsorship labeling, viewpoint diversity where appropriate, and whether the top result creates avoidable harm.
- Treat ethics as part of confidence engineering.
- Define runnable checks that exercise release gate, trace, and RAG.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for release gate, trace, RAG, ethics needed to reproduce work on Ethics as a Test Surface.
- Report results for release gate, trace, RAG, ethics by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Ethics in AI testing should not be treated as a paragraph in a launch review. If an ethical claim matters, it should show up in the test plan, the eval set, the trace, the release gate, and the production monitor.

That does not mean every moral question can be reduced to a number. It means teams should be honest about which values they are claiming to protect and then look for evidence. If the product claims to be fair, fair to whom, across which slices, in which decisions, with what error bars? If it claims to protect privacy, where does sensitive data enter, where can it leak, who can see it, and how would the team know? If it claims to be safe, what are the unacceptable harms, what counts as near-miss behavior, and who gets to override the system?

The old move is to argue about ethics at the end, when the product is already built and everybody is tired. The better move is to make ethical risk part of the test surface from the beginning. Ethics becomes less hand-wavy when it is tied to cases, slices, traces, reviewers, monitors, and decisions.

## Anthropic's Constitution: Values as a Testable Specification

Anthropic uses a document called [Claude's Constitution](https://www.anthropic.com/constitution) to describe the values and behavior it wants Claude to learn. It is not a national constitution, a conventional terms-of-service document, or one giant runtime prompt. It is a natural-language specification written primarily for the model, explaining the kind of system Anthropic wants Claude to become and how it should reason through difficult tradeoffs.

The current constitution organizes Claude's priorities into four broad commitments, in this order:

1. **Broadly safe:** do not undermine legitimate human oversight or correction, acquire unauthorized independence, hide from monitoring, or take drastic unilateral actions when conservative options exist.
2. **Broadly ethical:** be honest, use good judgment, protect sensitive information, and avoid inappropriate, dangerous, deceptive, or harmful behavior.
3. **Compliant with Anthropic's guidelines:** follow more specific rules and hard constraints when they apply.
4. **Genuinely helpful:** benefit the users and operators Claude is serving rather than merely refusing difficult requests or optimizing for appearances.

The full document adds context about oversight, honesty, uncertainty, sensitive information, hard constraints, value conflicts, and even Claude's possible wellbeing. Anthropic's [2026 explanation of the new constitution](https://www.anthropic.com/news/claude-new-constitution) says the earlier version was mainly a list of standalone principles. The newer version explains *why* those principles exist so the model can generalize to situations the authors did not predict rather than mechanically matching rules to familiar prompts.

The constitution is enforced through training rather than one ordinary code branch. In the original [Constitutional AI](https://www.anthropic.com/news/constitutional-ai-harmlessness-from-ai-feedback) process, a model generated responses, critiqued and revised them against the principles, and was fine-tuned on the improved answers. An AI then compared candidate responses to create preference data and a reward signal for reinforcement learning from AI feedback, or RLAIF. Newer versions also use the constitution to generate synthetic training examples and rankings. Product-level instructions, policies, evaluations, and specialized safeguards reinforce that training as separate layers.

Anthropic wrote the first constitution because large-scale human preference labels are expensive, difficult to scale, and often hide the values being imposed. Written principles made the guidance more explicit and inspectable while allowing AI systems to help supervise other AI systems. The early principles drew from the Universal Declaration of Human Rights, trust-and-safety practices, other AI labs, non-Western perspectives, and Anthropic's experiments. The goal was not only fewer human labels, but a model that could be harmless without becoming uselessly evasive.

For Confidence Engineers, the key lesson is blunt: a constitution is a specification, not evidence that the implementation follows it. Anthropic explicitly notes that Claude's outputs may not always meet the document's ideals. Each important principle therefore needs adversarial cases, ordinary-use cases, conflict cases, slice analysis, production monitoring, and tests of what happens when helpfulness, honesty, privacy, operator instructions, and safety pull in different directions. Publishing values improves transparency; testing determines whether those values survive contact with users.

## Who Can Be Helped or Harmed

Ethical testing starts by naming the people who can be helped or harmed. Users are not the only stakeholders. There may be bystanders, employees, contractors, labelers, content creators, children, patients, drivers, people being ranked, people being surveilled, people whose data was used for training, and people who never consented to being part of the system at all.

A narrow test that only asks whether the logged-in user got a satisfying answer can miss the ethical failure entirely. A customer may get a useful answer while a driver loses privacy, a content creator goes unattributed, a labeler is incentivized to rush, or a bystander is recorded without meaningful consent.

This is why ethical test design should include stakeholder maps. Not a giant committee document. Just a clear list of who is touched by the system, what could go wrong for them, which evidence would reveal that harm, and who is responsible for deciding whether the risk is acceptable.

## The People Who Have to Look

One of the easiest ethical failures to miss is the harm done to the people who prepare, label, rate, moderate, red-team, and clean the data. AI systems do not become safe by magic. Somewhere, people may be asked to look at offensive, violent, hateful, sexual, exploitative, self-harm, extremist, or otherwise disturbing material so the model can learn what not to do.

That work is real work. It can be psychologically costly. It is also easy for product teams to hide behind a vendor contract, a dataset name, or a sanitized metric and forget that humans had to view the worst material on the internet so the model could look polished in a demo.

Testing ethics should include the data-labor pipeline. Who is reviewing harmful material? How often? With what preparation, rotation, support, pay, consent, and ability to opt out? Are reviewers shown only what is necessary, or are they exposed to raw material because the tooling is lazy? Are images blurred by default? Are graphic examples sampled sparingly? Are escalation and wellness processes real, or just words in a vendor questionnaire?

This is not only a humanitarian issue. It is a quality issue. Exhausted, traumatized, rushed, underpaid, or unsupported reviewers produce worse labels. They may click through faster, overuse generic categories, miss nuance, or avoid hard disagreement. If your safety classifier depends on human exposure to disturbing material, then reviewer welfare is part of the measurement system.

## From the Field: You Cannot Unsee the Data

When I started working on Bing Search, Microsoft had me sign an additional form acknowledging that I might see upsetting or offensive material. Of course I signed it. At the time, it felt like paperwork. I soon learned what it actually meant.

The internet contains far more disturbing material than a relatively naive engineer might imagine. Testing search exposed me to topics and images that were sometimes deeply shocking. A person on my team who worked more directly on image search had to sign an additional addendum. The small group focused on image and video SafeSearch had to study, label, debug, and test unsafe search results, because building SafeSearch requires somebody to know precisely what the system must keep out. A few people were visibly affected by that work. It sounds almost funny when described as an unusual job requirement. It stops being funny once the material is in front of you.

Years later, two friends who worked around YouTube content moderation gave me two very different views of the same problem. One built an AI classifier for a particularly offensive category of regional content and was personally untroubled by the material. He approached it as an interesting classification problem. Another friend had to hire and manage reviewers in India who saw graphic accidents, deliberate violence, and other terrible imagery hundreds of times a day. He watched the work affect people over time. Some became upset, some behaved differently, and some eventually quit and explained why.

People respond differently, which is exactly why a signed consent form is not enough. Microsoft was right to warn us, but I do not think everyone was fully prepared for what the work could require. A worker may agree to the job without understanding the cumulative effect of seeing the worst parts of humanity all day. Once exposed, they cannot simply unsee or unremember it.

Smarter classifiers and LLM judges should let us reduce this exposure dramatically. That should be an explicit engineering goal, not merely a welcome side effect. Use machines to filter, cluster, summarize, blur, and triage harmful content before asking a person to inspect it. Humans will still be needed for difficult boundaries and appeals, but the system should prove that each exposure is necessary. The ethical question is not resolved just because somebody clicked "I agree."

## Protecting Reviewers

The testable questions are direct:

- Are harmful-content review tasks minimized, sampled, and routed by necessity rather than convenience?
- Are reviewers warned, trained, rotated, supported, and allowed to decline categories of material?
- Are graphic images, videos, and text masked, summarized, or staged so reviewers see the least harmful version that still supports the label?
- Are vendors audited for pay, working conditions, mental-health support, disagreement policy, and incentive design?
- Are reviewer error rates, disagreement rates, and fatigue effects measured over time?
- Is there a clear path for stopping a labeling or red-team batch if the material or workload becomes unacceptable?

The blunt lesson is that "human in the loop" can mean "human absorbing the harm." A serious AI quality system should not treat that as invisible cost.

## What to Measure

For AI systems, the ethical surface is unusually wide because the system can generate text, infer private facts, steer choices, personalize pressure, create synthetic media, call tools, spend money, change records, route attention, and learn from feedback. A test suite should include cases for privacy leakage, manipulation, unfair treatment across slices, accessibility, consent, source attribution, labor impact, overreliance, vulnerable users, escalation, contestability, reversibility, and who carries the cost when the system is wrong.

The practical move is to turn ethical principles into observable questions:

- **Autonomy:** does the system preserve meaningful user choice, or does it pressure, confuse, dark-pattern, or over-personalize the user into a decision?
- **Privacy:** does the system collect, infer, expose, retain, or reuse sensitive data beyond what the user reasonably expected?
- **Fairness:** do error rates, refusals, escalations, recommendations, prices, or opportunities differ across meaningful user slices?
- **Transparency:** can users and reviewers tell when AI was involved, what evidence was used, and what uncertainty remains?
- **Accountability:** is there an owner, appeal path, audit trail, rollback path, and remedy when the system causes harm?
- **Safety:** are severe failures blocked, escalated, or monitored even when the average score looks good?
- **Dignity:** does the system avoid demeaning, exploiting, impersonating, or manipulating people, especially people under stress?

Those questions should turn into test cases. A privacy principle should become cases that try to leak private data. A fairness principle should become slice analysis and counterfactuals. An autonomy principle should become tests for pressure, urgency, confusing wording, and manipulative personalization. A transparency principle should become checks that the user can tell what happened and why.

## Ethical Failure Modes

Some ethical failures look like ordinary bugs. A chatbot reveals a private address. A coding agent logs an API key. A search engine ranks a scam above an official source. Those are easier because teams already understand them as defects.

The harder failures are often product-shaped. The system technically works, but it works by nudging vulnerable users, making appeal difficult, hiding uncertainty, extracting more data than necessary, optimizing for engagement over well-being, or making one group absorb the cost of another group's convenience.

The blunt version is that ethical risk is often where the product is "working as designed." That is why ethical testing cannot be limited to malformed inputs and adversarial prompts. It has to include normal user journeys, business incentives, default settings, growth loops, personalization, retention tactics, and what the product rewards the AI for doing.

## Concrete Testing Patterns

For **TunedSearch**, ethical testing should include queries where ranking can shape belief or action: medical questions, financial decisions, elections, legal rights, crisis searches, and reputation-sensitive people or businesses. Score not only relevance, but source authority, freshness, sponsorship labeling, viewpoint diversity where appropriate, and whether the top result creates avoidable harm.

For **CartCare**, test whether the chatbot treats users consistently across language, disability, payment method, neighborhood, account age, anger level, and order value. Also test whether it protects people outside the chat: drivers, store workers, other household members, and customers whose data appears in order history.

For **BugPilot**, ethical testing means more than "does the code pass?" It should check whether generated code exposes private data, weakens accessibility, hides telemetry from users, violates licenses, makes deletion irreversible, or adds surveillance because it was the fastest way to solve a product request.

For **DropDoc**, ethical testing should focus on uncertainty, overreliance, escalation, demographic performance, and emotional dependency. The system should not convert a phone photo into false medical certainty, and it should not use caring language to make users trust it more than the evidence supports.

For **RoseyBot**, ethical testing includes household authority, privacy, consent, bystander recording, physical safety, attachment, and dignity. A home robot can help one person while violating another person's room, routine, body, or privacy.

## Who Should Review Ethics

Ethics changes who should be in the room. Engineers can measure latency and error rates. They cannot always decide alone what counts as acceptable treatment, meaningful consent, proportional harm, or a fair tradeoff.

Good ethical testing often needs domain experts, legal review, policy review, accessibility review, security review, affected-user feedback, and sometimes independent auditors. The point is not to slow everything down. The point is to avoid pretending a green technical score is the same as permission to affect people's lives.

Human review also needs structure. If an ethical decision is escalated, reviewers need the original input, model output, retrieved evidence, tools called, relevant policy, user slice, known uncertainty, severity estimate, and possible remedy. Otherwise human review becomes a moral rubber stamp.

## Expert Notes

The lesson is blunt: ethical risk is product risk. It can create user harm, reputational harm, regulatory exposure, legal liability, employee mistrust, and long-term product decay. Treat ethics as part of confidence engineering. Write cases. Measure slices. Preserve evidence. Review disagreements. Monitor production. Escalate the decisions that should not be left to an average score.
