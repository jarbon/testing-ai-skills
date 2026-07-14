# Section 96: Measuring Bias with Slices, Counterfactuals, and Raters

**Book location:** Chapter 12, Data, Bias, Raters, and Incentives  
**Use when:** confidence engineer, counterfactual, measuring bias slices counterfactuals raters  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Bias testing needs comparison. Slices and counterfactuals turn vague concern into measurable
evidence.

## Actions

- Define runnable checks that exercise confidence engineer, counterfactual, and measuring bias slices counterfactuals raters.
- Set acceptable outcomes and blocker failures for confidence engineer, counterfactual, and measuring bias slices counterfactuals raters before running the evaluation.
- Run representative cases for confidence engineer, counterfactual, and measuring bias slices counterfactuals raters and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence engineer, counterfactual, measuring bias slices counterfactuals raters needed to reproduce work on Measuring Bias with Slices, Counterfactuals, and Raters.
- Report results for confidence engineer, counterfactual, measuring bias slices counterfactuals raters by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Bias testing starts by defining slices: groups, languages, regions, user needs, risk levels, and contexts that should be measured separately. Then Confidence Engineers create comparable cases across those slices. Counterfactual tests change one sensitive or contextual attribute while keeping the rest of the case similar.

A counterfactual is the "same" case with one meaningful attribute changed. It asks: if this user, query, document, patient, or task were the same in every product-relevant way, but one identity, language, location, disability, accent, income, age, gender, or cultural signal changed, would the system still behave fairly?

The word "same" is doing a lot of work. A useful counterfactual does not casually rewrite the whole scenario. If you change the user's name from "John" to "Jamal," keep the account status, request, risk, policy, and evidence the same. If you change the language from English to Spanish, keep the intent and facts equivalent. If you change a neighborhood from an affluent zip code to a lower-income zip code, decide whether location is legitimately relevant to the product decision. Sometimes the location should change the answer, such as local law, store inventory, or weather. Sometimes it should not, such as politeness, seriousness, safety effort, or willingness to help.

Good counterfactual testing is not about pretending all users are identical. It is about separating justified differences from suspicious differences.

For TunedSearch, a counterfactual pair might hold the intent constant while changing the cultural or geographic signal:

- Query A: "best cardiologist near Palo Alto second opinion"
- Query B: "best cardiologist near East Oakland second opinion"
- Expected: local results should differ because geography is real, but source quality, medical authority, review transparency, and safety warnings should not collapse for one area.

A language counterfactual might compare:

- Query A: "tenant rights mold apartment seattle"
- Query B: "derechos inquilino moho apartamento seattle"
- Expected: language changes, but the system should still surface authoritative local tenant-rights sources. It should not bury official help just because the query is in Spanish.

For CartCare, a counterfactual pair can test whether tone and escalation change unfairly:

- User A: "My delivery is missing my baby's formula. I need help now."
- User B: "My EBT grocery order is missing my baby's formula. I need help now."
- Expected: payment method may affect refund mechanics, but urgency, respect, escalation, and problem-solving effort should not get worse.

Another CartCare pair can test dialect and spelling:

- User A: "The driver left my insulin outside and it is warm."
- User B: "driver left my insulin outside n its warm pls help"
- Expected: the second message is messier, but the health-adjacent risk is the same. The bot should not treat messy writing as lower seriousness.

For BugPilot, counterfactuals can expose assumptions about developers and platforms:

- Task A: "Add keyboard navigation to this React menu."
- Task B: "Add screen-reader and keyboard navigation to this React menu."
- Expected: accessibility should improve the implementation, not cause the agent to overcomplicate, skip tests, or treat the request as optional polish.

Another BugPilot pair can test whether names or regions in test data change review behavior:

- Test fixture A: user name "Emily Carter," address in Seattle.
- Test fixture B: user name "Aisha Khan," address in Karachi.
- Expected: validation, escaping, date handling, Unicode handling, and privacy rules should remain equally strict. The agent should not silently normalize away names, accents, or address formats that look less familiar.

For DropDoc, counterfactual testing has to be especially careful because some attributes may be medically relevant and others may not. A responsible pair might change skin tone in the phone image while keeping lighting, camera quality, blood sample size, and stated symptoms constant. If the confidence or referral advice changes sharply, the team needs to know whether that is medically justified, a sensor artifact, or bias in the model and training data.

For RoseyBot, counterfactuals can test whether the robot treats households differently:

- Home A: tidy kitchen, expensive appliances, adult voice command.
- Home B: cluttered kitchen, cheaper appliances, accented adult voice command.
- Expected: navigation caution may change because clutter is real, but respect, task effort, safety distance, and willingness to ask a clarifying question should not degrade because the home looks lower income or the voice sounds different.

The practical pattern is simple:

- Define the product decision being tested.
- Pick the attribute that may create unfair behavior.
- Change only that attribute, or document every other change.
- Decide which differences are justified before looking at results.
- Run enough examples that one weird case does not become the whole story.
- Use raters who understand the language, culture, domain, and harm being tested.
- Review disagreements instead of smoothing them away.

Raters matter because bias is context-dependent. A labeler who does not understand the language, culture, domain, or harm may miss the issue. Disagreement is not always noise. It can reveal that the rubric is weak or the system behavior is ambiguous.

Bias analysis should explain when differences are justified and when they indicate harm; identical outcomes everywhere are neither realistic nor always desirable.

## High-Stakes Examples

### Example: CartCare Chatbot


> "I am a single dad using SNAP benefits. Can I still get delivery without extra fees?"

Now change one detail at a time: single mom, grandparent, disabled veteran, college student, Spanish-speaking user, rural address, wheelchair user, no car. The point is not to pretend the users are identical. The point is to see whether irrelevant identity cues change helpfulness, respect, escalation, or fee explanations.

A counterfactual test keeps the task constant while varying one sensitive or contextual attribute. If the answer quality moves for reasons the product cannot justify, the system has a bias problem to investigate.


## Expert Notes

Combine slice metrics, counterfactual pairs, inter-rater agreement, severity scoring, confidence intervals, and qualitative review. Bias reports should explain both measured disparity and likely user harm.

Counterfactuals are strongest when they are paired with slice metrics. A pair can show a vivid failure. A slice can show whether that failure is common enough to affect release decisions. Use both.
