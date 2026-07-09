# Case Study — Posting Group Mismatch (Inventory → G/L)

## Summary
Incorrect General Product Posting Group caused wrong COGS postings, impacting financial reporting.

## Problem
Sales shipments posted COGS to a generic expense account.

## Root Cause
Item Card → General Product Posting Group = RAW-MAT instead of FINISHED.

## Resolution
1. Updated Item Card → FINISHED.
2. Validated General Posting Setup mapping.
3. Reposted test transactions in Sandbox.
4. Verified corrected G/L entries.

## Prevention
- Posting Group Matrix
- QC checklist for item creation

## Evidence
Screenshots: Item Card, General Posting Setup, Value Entries.
