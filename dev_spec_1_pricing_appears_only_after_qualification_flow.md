# Pricing appears only after qualification flow — dev spec
Site: nomadinternet.com · Priority 1 · High · Effort: Medium (2-5 days)

## Problem
No pricing is shown until the visitor completes the coverage/qualification form, so cost is discovered late in the journey.

## Evidence (from the live site)
> h1: Let's Get You the Right Internet
> ctas: CHECK COVERAGE | CHECK IF IT WORKS AT MY ADDRESS | SEE MY OPTIONS | GET STARTED | START CHAT | SEE WHAT I QUALIFY FOR | CHECK MY COVERAGE
> form: submit=CONTINUE (field extraction is unreliable on this site — raw HTML carries 5 field(s); do not claim fields or labels are missing)

## Current state
h1: Let's Get You the Right Internet; cta: Check Coverage; notes: No pricing visible before qualification form.

## Required change
h1: Plans and Pricing; cta: See Plans; notes: Display starting prices or price range before qualification form.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Display starting prices or price range before qualification form.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_pricing_appears_only_after_qualification_flow` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
