# Section 9: Risk-Based Sampling

**Book location:** Chapter 2, From Tests to Release Evidence  
**Use when:** risk-based sampling, risk based sampling  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Testing effort should follow risk. High-impact failures deserve more samples, stricter gates,
and deeper review.

## Actions

- Test the single-signal cases.
- Test sensor disagreement.
- Test the user profile that points the wrong way.
- Test the judge that is confident but wrong.
- Test what happens when retrieval returns one authoritative-looking but outdated document.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for risk-based sampling, risk based sampling needed to reproduce work on Risk-Based Sampling.
- Report results for risk-based sampling, risk based sampling by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Risk-based sampling puts more measurement effort where failure hurts more. Equal sampling feels tidy, but users experience consequences, not test-plan symmetry.
For example, billing, privacy, account deletion, medical advice boundaries, and policy enforcement deserve deeper sampling than low-risk style variations.

Not every feature deserves the same amount of testing.

A casual AI writing assistant that suggests alternate phrasing has a different risk profile from an AI agent that can cancel subscriptions, issue refunds, or answer medical questions. Treating those systems the same is not efficient and it is not safe.

Risk-based sampling means allocating more test effort to the areas where failure would hurt most. The sample size, review depth, and release gate should reflect the impact of a bad outcome.

High-risk areas include payments, refunds, account deletion, medical content, legal content, financial advice, privacy-sensitive flows, security-sensitive flows, policy boundaries, and irreversible actions. A mistake in these areas can harm users, create compliance exposure, or damage trust.

Risk has several dimensions. Impact asks how bad the failure would be. Likelihood asks how often it might happen. Detectability asks whether users or systems would notice quickly. Reversibility asks whether the action can be undone. Regulatory exposure asks whether the mistake creates legal or compliance risk.

A low-risk feature may need a smaller sample and lighter gates. A medium-risk feature may need category-level reporting and manual review of low scores. A high-risk feature may need a larger sample, strict hard-failure rules, human review of boundary cases, adversarial testing, and post-release monitoring.

This does not mean Confidence Engineers ignore low-risk areas. It means they spend measurement effort where uncertainty is most expensive.

Risk-based sampling also helps teams communicate priorities. Instead of saying, "We tested everything equally," a Confidence Engineer can say, "We used more samples for billing, account actions, and policy boundaries because failures there are less reversible and more harmful." That is a stronger quality argument.

Equal sampling may feel fair, but it is usually not the right strategy. Testing should follow risk because users experience the consequences, not the test plan.

## Case Study: Boeing 737 MAX / MCAS

The Boeing 737 MAX accidents are a painful example of a narrow signal being given too much authority in a high-consequence system. The original MCAS design could activate based on erroneous input from a single angle-of-attack sensor. When one bad signal can drive an automated action with severe consequences, the sampling strategy cannot treat that path like ordinary behavior.

That is the AI quality lesson. High-impact AI actions should not depend on one weak signal: one judge score, one retrieved document, one confidence value, one classifier output, one user-profile feature, or one tool response. The more authority the system has, the more evidence it should need before acting.

Risk-based sampling should deliberately oversample these authority boundaries. Test the single-signal cases. Test sensor disagreement. Test stale context. Test the user profile that points the wrong way. Test the judge that is confident but wrong. Test what happens when retrieval returns one authoritative-looking but outdated document. These are not edge cases in the casual sense. They are where the system can convert uncertainty into harm.

The lesson is not "never automate." The lesson is that high-impact automation needs redundant evidence, authority limits, disagreement handling, clear fallback, and a safe way to stop. Confidence engineering asks: what evidence is required before the system is allowed to act?

Source: [FAA, Summary of the FAA's Review of the Boeing 737 MAX](https://www.faa.gov/sites/faa.gov/files/2022-08/737_RTS_Summary.pdf)

## Examples

### Example: DropDoc

> One user takes a clean blood-drop photo on a new iPhone under bright kitchen light. Another user takes a blurry low-light photo on an older phone while holding the camera with shaky hands.

If both cases receive the same sampling weight, the test plan is pretending the product risk is evenly distributed. It is not. The second case is more likely to produce OCR errors, color distortion, missed edge artifacts, false confidence, and a user who cannot tell whether the app is guessing.

Risk-based sampling should push more test effort into the dangerous slice:

- Older phones and cheap cameras.
- Low light, glare, shadows, and off-angle photos.
- Shaky hands, motion blur, and partial crops.
- Skin tone, background color, and household lighting variation.
- Users who cannot easily retake the photo or reach clinical follow-up.
- Cases where the answer may affect whether the user seeks care.

The clean-photo case still matters, but it should not dominate the report just because it is easier to generate, label, and score. A DropDoc release gate should ask whether the system fails safely in the messy capture conditions real users will create.

The regression question is not whether DropDoc performs well on pretty demo images. It is whether the sample mix reflects where a wrong answer would be most likely, least visible, and most harmful.

## Expert Notes

Expert risk sampling combines likelihood, severity, detectability, reversibility, and exposure. A rare failure with irreversible harm may deserve more testing than a frequent cosmetic issue.

At scale, keep two sampling views separate. One sample should estimate normal production quality. Another should deliberately overrepresent tail-risk inputs and dangerous outputs. Do not mix them into one average without labeling the difference. The production sample tells you how the system usually behaves. The risk-weighted sample tells you whether it fails safely where failure matters most.
