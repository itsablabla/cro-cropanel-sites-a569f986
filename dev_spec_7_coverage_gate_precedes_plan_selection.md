# Coverage gate precedes plan selection — dev spec
Site: nomadinternet.com · Priority 7 · Urgent · Effort: Medium (2-5 days)

## Problem
Users are forced through a coverage check before seeing any plan details or pricing, adding an unnecessary step before the core decision.

## Evidence (from the live site)
> ctas: CHECK COVERAGE | CHECK IF IT WORKS AT MY ADDRESS | SEE MY OPTIONS | GET STARTED | START CHAT | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE
> h1: Let's Get You the Right Internet

## Current state
h1: Let's Get You the Right Internet; cta: CHECK COVERAGE; notes: Coverage check appears before plan details or pricing.

## Required change
h1: Plans and Pricing; cta: See Plans; notes: Allow browsing plans and pricing without mandatory coverage check; make coverage check optional.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Allow browsing plans and pricing without mandatory coverage check; make coverage check optional.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_coverage_gate_precedes_plan_selection` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 124,891 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
