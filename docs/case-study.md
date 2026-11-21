# Case study: Spend Lens

## The problem

Banking apps show a list of transactions and a pie chart. They rarely tell you, on the 18th, that groceries are on pace to go over, or that you pay for six subscriptions. Budgeting apps that do this want your bank login. Many people would rather not give that to anyone.

## Approach

The hard part of tools like this is not the charts. It is getting real, messy files in without friction, and earning enough trust that people put their data in at all. So I started from the import and the privacy model, then built the views a user would check every week. The main decisions:

### 1. Import CSV exports, never ask for a bank login

Open banking connections give fresh data but need a licensed provider, and many people do not want to hand over bank access.

**Decision:** Spend Lens reads the CSV export every bank offers. The file is read in the browser and stored there.

Full record: [docs/decisions/0001-csv-not-bank-login.md](decisions/0001-csv-not-bank-login.md)

### 2. Categorise with rules the user can see and edit, not a model

A model guesses well on average but cannot explain why a payment landed in a category, and users stop trusting it after the first odd guess.

**Decision:** Built-in keyword rules for common Polish shops and services, plus the user's own rules, which always win. One correction can become a rule for that place.

Full record: [docs/decisions/0002-rules-you-can-see.md](decisions/0002-rules-you-can-see.md)

### 3. Warn when a category is on pace to go over, not only when it is over

A budget alert on the 29th is too late to act on.

**Decision:** For the current month, the app projects each category's spending to month end at the current pace and warns above the budget, with what is left and how many days remain.

Full record: [docs/decisions/0003-warn-on-pace-not-only-over.md](decisions/0003-warn-on-pace-not-only-over.md)

## What it does

- **Import:** any bank CSV. Polish and English column names are recognised, as are UTF-8 and Windows-1250 files, lines above the header, semicolons, "1 234,56" amounts, and separate money out and money in columns. A preview shows what will be imported. Importing the same file twice adds nothing.
- **Categories:** built-in rules for common shops and services in Poland, and your own rules first. Change a category once, choose "Yes, remember", and it applies to past and future payments at that place.
- **Month:** money in, spending, left over and share kept, against the 3-month average. Spending by category against budgets, a 6-month chart and the biggest places.
- **Early warnings:** a category over budget, a category on pace to go over by month end, and unusually large payments.
- **Budgets:** a limit per category, with your own averages as hints and one tap to fill them.
- **Subscriptions:** regular payments found by pattern (same place, at least 3 of the last 6 months, similar amount), with the monthly and yearly cost.
- **Data:** export with categories as CSV, JSON backup and restore, and made-up sample data, clearly marked.

## How it was tested

Every flow was clicked through on desktop and phone widths, with the made-up sample data and with test files built to be awkward: semicolons, European number formats, lines above the header, Windows-1250 encoding and separate money out and in columns. Problems found and fixed before release included Polish letters breaking in place names, city names splitting the same shop into several places, and a table that did not fit on a phone.

## What I would measure

No usage data yet, so there are no findings. These are hypotheses to test with real users.

| Measure | Definition | Target |
|---|---|---|
| Coverage | Share of spending left in Other after the first import, and after a month of corrections | [x]% |
| Return use | Share of users who import a second month | [x]% |
| Action | Share of users who change or cancel at least one regular payment found | [x]% |

## What I would do next

1. Split a payment across categories
2. Shared budgets for two people from two exports
3. Better place names with a small dictionary of Polish card descriptors

## My role

I defined the problem, the users, the features and the decisions, and tested every flow. Claude (Anthropic) wrote the code with me. The idea started from an example in Justin McKelvey's list of vibe coding projects, which I turned into a full app with my own product choices.
