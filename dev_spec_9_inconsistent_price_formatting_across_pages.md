# Inconsistent price formatting across pages — dev spec
Site: nomadinternet.com · Priority 9 · Medium · Effort: Medium (2-5 days)

## Problem
Price display formats vary across plan pages (e.g., '/month' vs 'one-time', inconsistent currency formatting), causing confusion.

## Evidence (from the live site)
> h2: $99.95 /month
> h2: $129.95 /month
> h2: $0.00 (one-time)
> h2: $99.99 (one-time)
> prices: $99.95/month $129.95/month $99.95/mo $0.00 $99.95 $99.99

## Current state
h1: Plans; cta: Check Coverage; notes: Inconsistent price formatting across plans pages.

## Required change
h1: Plans; cta: Check Coverage; notes: Standardize price display format (e.g., always use '/month' and consistent currency).

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Standardize price display format (e.g., always use '/month' and consistent currency).
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_inconsistent_price_formatting_across_pages` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
