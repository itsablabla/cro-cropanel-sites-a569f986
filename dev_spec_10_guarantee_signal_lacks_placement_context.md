# Guarantee signal lacks placement context — dev spec
Site: nomadinternet.com · Priority 10 · Medium · Effort: Low (0.5-2 days)

## Problem
A confidence-related heading exists on the rural-internet page but no equivalent appears on the plans pages, leaving shoppers without reassurance at the point of commitment.

## Evidence (from the live site)
> h2: SHOP WITH CONFIDENCE

## Current state
h1: Rural Internet; cta: Check Coverage; notes: SHOP WITH CONFIDENCE section only on rural-internet page.

## Required change
h1: Plans; cta: Check Coverage; notes: Replicate SHOP WITH CONFIDENCE section on plans pages.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Replicate SHOP WITH CONFIDENCE section on plans pages.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_guarantee_signal_lacks_placement_context` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
