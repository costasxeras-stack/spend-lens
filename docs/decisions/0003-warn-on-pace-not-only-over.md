# 0003: Warn when a category is on pace to go over, not only when it is over

**Status:** accepted, 0.1.0

## Context

A budget alert on the 29th is too late to act on.

## Decision

For the current month, the app projects each category's spending to month end at the current pace and warns above the budget, with what is left and how many days remain.

## Tradeoff

- Gives time to act.
- Spending is not even across a month, so the early warning can be wrong in either direction. The wording says "on pace for", not "will".
- Large one-off payments trigger it. They also get their own alert, so the cause is clear.
