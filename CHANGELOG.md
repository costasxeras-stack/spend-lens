# Changelog

All notable changes to this project. Versions follow [docs/versioning.md](docs/versioning.md).

## [0.1.0] - 2026-11-21

First release.

### Added
- Import: any bank CSV. Polish and English column names are recognised, as are UTF-8 and Windows-1250 files, lines above the header, semicolons, "1 234,56" amounts, and separate money out and money in columns. A preview shows what will be imported. Importing the same file twice adds nothing.
- Categories: built-in rules for common shops and services in Poland, and your own rules first. Change a category once, choose "Yes, remember", and it applies to past and future payments at that place.
- Month: money in, spending, left over and share kept, against the 3-month average. Spending by category against budgets, a 6-month chart and the biggest places.
- Early warnings: a category over budget, a category on pace to go over by month end, and unusually large payments.
- Budgets: a limit per category, with your own averages as hints and one tap to fill them.
- Subscriptions: regular payments found by pattern (same place, at least 3 of the last 6 months, similar amount), with the monthly and yearly cost.
- Data: export with categories as CSV, JSON backup and restore, and made-up sample data, clearly marked.
