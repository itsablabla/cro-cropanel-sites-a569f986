# Multiple qualification CTAs compete — dev spec
Site: nomadinternet.com · Priority 6 · Medium · Effort: Medium (2-5 days)

## Problem
Multiple qualification and coverage CTAs on the same viewport overload visitors with choices, delaying the primary conversion path.

## Evidence (from the live site)
> ctas: CHECK COVERAGE | CHECK IF IT WORKS AT MY ADDRESS | SEE MY OPTIONS | GET STARTED | START CHAT | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE
> ctas: CHECK COVERAGE | Watch on | SEE WHAT I QUALIFY FOR | START CHAT | CHECK MY COVERAGE

## Current state
h1: Let's Get You the Right Internet; cta: Multiple CTAs; notes: Multiple qualification CTAs compete for attention.

## Required change
h1: Let's Get You the Right Internet; cta: Check Coverage; notes: Reduce to one primary qualification CTA per viewport.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Reduce to one primary qualification CTA per viewport.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_multiple_qualification_ctas_compete` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
