# Quadrent Case Study — VAT Posting Setup Configuration Error & Resolution
**System:** Dynamics 365 Business Central  
**Company:** Quadrent Sports Apparel (No‑Data Sandbox)  
**Module:** Financials → VAT Posting Setup  
**Author:** Hasan Farooqui  
**Date:** 10 July 2026  

---

## 1. Summary
During initial VAT configuration in a No‑Data Business Central company, multiple validation errors occurred due to missing VAT G/L accounts, missing G/L Account Subcategories, and duplicate VAT Identifiers.  
This case study documents the error, root cause, and resolution steps, with screenshots captured before and after correction.

---

## 2. Background
Quadrent Sports Apparel is a fresh No‑Data company.  
This means:

- No VAT Posting Groups  
- No VAT Posting Setup  
- No VAT G/L Accounts  
- No Account Subcategories  
- No VAT Identifiers  

All VAT structure must be created manually.

---

## 3. Error Encountered

### 3.1 VAT Posting Setup Error
When creating VAT Posting Setup rows, Business Central displayed:

- Yellow notification bar  
- Inline red error icons  
- Missing VAT Identifier  
- Missing Sales VAT Account  
- Duplicate VAT Identifier conflict  

**Cause:**  
BC requires:

- Unique VAT Identifier per VAT %  
- Valid Sales VAT Account  
- Valid Purchase VAT Account  
- Valid Account Subcategory for VAT accounts  

These did not exist yet.

📸 **Screenshot 01 — VAT Posting Setup Error**  
![VAT Posting Setup Error](/02-Support-Case-Studies/04-VAT-Posting-Setup-Error/01_Error.jpg)

---

### 3.2 G/L Account Card Error
When creating **2250 – Sales VAT 23%**, BC displayed:

- Red error icon beside **Account Subcategory: VAT**  
- Yellow bar indicating page validation failure  

**Cause:**  
The subcategory **VAT** did not exist under Liabilities.

📸 **Screenshot 02 — G/L Account Card Error**  
*(Insert screenshot here)*

---

### 3.3 G/L Account Categories Error
Opening **G/L Account Categories** showed:

- VAT category missing  
- Red error icon  
- Yellow bar  
- Category incomplete (missing Additional Report Definition)

📸 **Screenshot 03 — G/L Account Categories Error**  
*(Insert screenshot here)*

---

## 4. Resolution Steps

### 4.1 Create VAT G/L Accounts
Two VAT accounts were created:

| No. | Name | Category | Subcategory | Type |
|-----|-------|-----------|--------------|--------|
| **2250** | Sales VAT 23% | Liabilities | VAT | Posting |
| **3250** | Purchase VAT 23% | Liabilities | VAT | Posting |

📸 **Screenshot 04 — Validated G/L Account Card (2250)**  
*(Insert screenshot here)*

---

### 4.2 Create Missing VAT Subcategory
In **G/L Account Categories**, a new category was added:

- **Description:** VAT  
- **Account Category:** Liabilities  
- **Additional Report Definition:** Operating Activities  

This resolved the G/L Account Card validation error.

📸 **Screenshot 05 — VAT Category Created & Validated**  
*(Insert screenshot here)*

---

### 4.3 Correct VAT Posting Setup
Final VAT Posting Setup rows created:

| VAT Bus. PG | VAT Prod. PG | VAT % | VAT Identifier | Calc Type | Sales VAT | Purchase VAT |
|-------------|---------------|--------|----------------|------------|------------|----------------|
| DOMESTIC | EXPORT-0 | 0 | VAT0 | Normal VAT | 2250 | 3250 |
| DOMESTIC | LOCAL | 23 | LOCVAT | Normal VAT | 2250 | 3250 |
| DOMESTIC-23 | DOMESTIC-23 | 23 | VAT23 | Normal VAT | 2250 | 3250 |
| EU | EU | 0 | RCO | Reverse Charge | 2250 | 3250 |

📸 **Screenshot 06 — Final Validated VAT Posting Setup**  
*(Insert screenshot here)*

---

## 5. Root Cause Analysis

| Issue | Root Cause | Resolution |
|-------|-------------|-------------|
| Missing VAT Identifier | No identifier created | Added unique identifiers (VAT23, VAT0, etc.) |
| Missing VAT Accounts | No G/L accounts existed | Created 2250 & 3250 |
| Missing VAT Subcategory | No VAT category under Liabilities | Created VAT category |
| Duplicate VAT Identifier | Same identifier used for different VAT % | Assigned unique identifiers |
| Page validation errors | Incomplete configuration | Completed all required fields |

---

## 6. Business Impact

### Before Fix
- VAT Posting Setup could not validate  
- Sales/Purchase transactions would fail  
- VAT calculation incorrect or blocked  
- Posting errors during invoicing  
- Financial reporting incomplete  

### After Fix
- VAT Posting Setup fully validated  
- Sales & Purchase VAT calculated correctly  
- Reverse Charge configured  
- G/L accounts mapped properly  
- System ready for transaction posting  

---

## 7. Consultant Commentary
This case demonstrates core MB‑800 skills:

- Understanding VAT Posting Setup structure  
- Creating VAT accounts from scratch  
- Resolving validation errors  
- Configuring VAT for domestic, export, and EU scenarios  
- Documenting errors and resolutions professionally  

This is exactly the type of troubleshooting expected from a Business Central Support Consultant.

---

## 8. Files & Evidence

```text
/02-Support-Case-Studies/04-VAT-Posting-Setup-Error/
│
├── 01_Error.png
├── 02_GLAccount_Error.png
├── 03_GLCategory_Error.png
├── 04_GLAccount_Resolved.png
├── 05_VATCategory_Resolved.png
└── 06_Final_VATPostingSetup.png
```

---

## 9. Status
✅ **Completed**  
System validated and ready for VAT‑related posting scenarios.



