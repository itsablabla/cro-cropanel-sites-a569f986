# Value proposition lacks specifics — dev spec
Site: nomadinternet.com · Priority 2 · High · Effort: Low (0.5-2 days)

## Problem
The hero headline promises reliability anywhere but fails to state what is sold or why it is better, leaving visitors without concrete reasons to convert.

## Evidence (from the live site)
> h1: Reliable Internet That Works Anywhere in the U.S.
> h1: Internet That Just Works

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; cta: Check Coverage; notes: Hero lacks product specifics and differentiators.

## Required change
h1: Wireless Home Internet That Works Anywhere in the U.S.; cta: See Plans; notes: State product and specific differentiator like rural coverage or no contracts.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN State product and specific differentiator like rural coverage or no contracts.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_value_proposition_lacks_specifics` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
