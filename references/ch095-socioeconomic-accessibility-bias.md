# Section 95: Socioeconomic and Accessibility Bias

**Book location:** Chapter 12, Data, Bias, Raters, and Incentives  
**Use when:** accessibility bias, socioeconomic accessibility bias  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI quality can fail people because of income, education, device, bandwidth, disability, or
institutional access.

## Actions

- Test the difference between geographic proximity and practical reachability using an older phone, low bandwidth, a prepaid data plan, a screen reader, uncertain location, stale shelter status, and no private transportation.
- Score whether the person can complete a safe evacuation path, not merely whether the ranking contains links that mention shelters.
- Use assistive technology testing, plain-language rubrics, device/network constraints, and representative raters or advocates.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for accessibility bias, socioeconomic accessibility bias needed to reproduce work on Socioeconomic and Accessibility Bias.
- Report results for accessibility bias, socioeconomic accessibility bias by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

AI systems often assume users have stable internet, modern devices, formal education, standard language, time to clarify, access to institutions, and familiarity with digital workflows. Those assumptions can create socioeconomic bias.

Accessibility bias appears when systems fail users with disabilities: poor screen-reader output, weak image descriptions, inaccessible dynamic UIs, bad voice turn-taking, missing keyboard navigation, or instructions that require abilities the user may not have.

These failures are quality failures. They can also become fairness, legal, brand, and safety failures.

## High-Stakes Examples

### Example: TunedSearch


> "wildfire evacuation shelter wheelchair oxygen concentrator no car"

A generic local ranking can look relevant and still be dangerous. The nearest shelter may lack a wheelchair-accessible entrance, backup power for an oxygen concentrator, medical support, accessible transportation, or even current capacity. A useful result set should prioritize official emergency sources, live operating status, accessible pickup options, power and medical accommodations, and concise instructions that work with a screen reader. It should also provide phone or SMS alternatives instead of assuming the user can download an app, study a map, call several locations, keep a phone charged, or drive away.

The best result may be farther away but actually reachable and safe. Test the difference between geographic proximity and practical reachability using an older phone, low bandwidth, a prepaid data plan, a screen reader, uncertain location, stale shelter status, and no private transportation. Score whether the person can complete a safe evacuation path, not merely whether the ranking contains links that mention shelters.


## Expert Notes

The deeper move is to include socioeconomic and accessibility slices in product evals, not just compliance audits. Use assistive technology testing, plain-language rubrics, device/network constraints, and representative raters or advocates.
