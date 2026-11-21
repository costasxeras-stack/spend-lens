# 0001: Import CSV exports, never ask for a bank login

**Status:** accepted, 0.1.0

## Context

Open banking connections give fresh data but need a licensed provider, and many people do not want to hand over bank access.

## Decision

Spend Lens reads the CSV export every bank offers. The file is read in the browser and stored there.

## Tradeoff

- No login, no third party, nothing to trust.
- Data is as fresh as the last export. Monthly is enough for budgeting.
- Each bank's format differs. Header detection and a preview with column matching handle that, instead of a list of supported banks.
