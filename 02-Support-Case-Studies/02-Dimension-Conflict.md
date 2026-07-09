# Case Study — Dimension Conflict on Sales Order

## Summary
Sales Orders blocked due to missing mandatory dimensions.

## Problem
Error: “Dimension Department Code is missing or invalid.”

## Root Cause
Customer default dimension not inherited due to incorrect Dimension Priority.

## Resolution
1. Updated Customer Card → Default Dimension.
2. Updated Dimension Priority.
3. Revalidated Sales Order.

## Prevention
- Dimension Rules SOP

## Evidence
Screenshots: Error message, Customer Card, Dimension Setup.
