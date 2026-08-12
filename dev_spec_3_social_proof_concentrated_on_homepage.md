# Social proof concentrated on homepage — dev spec
Site: nomadinternet.com · Priority 3 · High · Effort: Medium (2-5 days)

## Problem
Customer testimonials and press mentions appear only on the homepage and rural-internet page, not on plans pages where purchase decisions are made.

## Evidence (from the live site)
> h2: Real Stories from Real Users
> h2: As Featured In:
> h2: Real Stories from Real Users

## Current state
h1: Plans; cta: Check Coverage; notes: No social proof on plans pages.

## Required change
h1: Plans; cta: Check Coverage; notes: Add testimonials and press logos near pricing and CTAs.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add testimonials and press logos near pricing and CTAs.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_social_proof_concentrated_on_homepage` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
