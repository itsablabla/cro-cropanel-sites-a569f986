# Duplicate coverage form on page — dev spec
Site: nomadinternet.com · Priority 8 · Medium · Effort: Medium (2-5 days)

## Problem
The coverage check form appears twice on the same page, forcing visitors to encounter duplicate interaction points and potentially submit the same information twice.

## Evidence (from the live site)
> form: submit=CONTINUE (field extraction is unreliable on this site — raw HTML carries 5 field(s); do not claim fields or labels are missing)
> form: submit=CONTINUE (field extraction is unreliable on this site — raw HTML carries 5 field(s); do not claim fields or labels are missing)

## Current state
h1: Let's Get You the Right Internet; cta: CONTINUE; notes: Two identical coverage forms on the same page.

## Required change
h1: Let's Get You the Right Internet; cta: CONTINUE; notes: Consolidate to a single coverage form per page.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate to a single coverage form per page.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_duplicate_coverage_form_on_page` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
