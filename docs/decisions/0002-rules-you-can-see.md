# 0002: Categorise with rules the user can see and edit, not a model

**Status:** accepted, 0.1.0

## Context

A model guesses well on average but cannot explain why a payment landed in a category, and users stop trusting it after the first odd guess.

## Decision

Built-in keyword rules for common Polish shops and services, plus the user's own rules, which always win. One correction can become a rule for that place.

## Tradeoff

- Every category can be explained: this text matched this rule.
- New shops land in Other until the user teaches it. The Data tab shows how many are still in Other.
- Rules are per text, so a shop that sells many things gets one category.
