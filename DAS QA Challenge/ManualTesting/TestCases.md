# Test Cases - Random Date Generator

## Overview

This document contains manual test cases for the Random Date Generator component available at CodeBeautify.

https://codebeautify.org/generate-random-date

## Testing Techniques Used
- Functional Testing
- Boundary Value Analysis
- Negative Testing
- Exploratory Testing
- UI Validation
- Usability Testing

---

# Generate Random Date

## RDG-001 - Verify default values and initial generated output

**Priority:** High

**Test Steps**
1. Open the Random Date Generator page.

**Expected Result**
- Page loads successfully.
- Default values are displayed:
  - Number of dates = 10
  - Default format selected
  - Start/End dates populated
- 10 pre-generated dates are visible.

---

## RDG-002 - Verify Generate button refreshes output

**Priority:** High

**Test Steps**
1. Observe current output
2. Click "Generate Random Date"

**Expected Result**
- New dates are generated
- Previous output is replaced

---

## RDG-003 - Verify auto update on configuration change

**Priority:** Medium

**Test Steps**
1. Change number of dates
2. Change format
3. Change start/end date

**Expected Result**
- Output updates automatically

---

# Number of Dates

## RDG-004 - Generate 1 date
**Expected Result:** 1 date generated

## RDG-005 - Generate 10 dates
**Expected Result:** 10 dates generated

## RDG-006 - Zero input validation
**Expected Result:** Rejected or validated

## RDG-007 - Negative input validation
**Expected Result:** Rejected

## RDG-008 - Decimal input validation
**Expected Result:** Rejected or clearly defined rounding

## RDG-009 - Large input handling (9999)
**Expected Result:** No crash, validation or limit applied

## RDG-010 - Non-numeric input validation
**Expected Result:** Only numbers accepted

## RDG-011 - Empty input handling
**Expected Result:** Default restored or validation shown

---

# Date Output Format

## RDG-012 - ISO 8601 validation
**Expected Result:** Correct ISO format

## RDG-013 - Standard format validation
**Expected Result:** Matches selected format

## RDG-014 - Predefined formats validation
**Expected Result:** All formats applied correctly

## RDG-015 - Custom format validation
**Expected Result:** Tokens + literals respected

## RDG-016 - Custom format case sensitivity
**Expected Result:** Consistent handling or documented rule

---

# Start & End Date

## RDG-017 - Valid Start Date
**Expected Result:** Dates ≥ Start Date

## RDG-018 - Valid End Date
**Expected Result:** Dates ≤ End Date

## RDG-019 - Start equals End
**Expected Result:** Single exact date

## RDG-020 - Start > End validation
**Expected Result:** Error shown

## RDG-021 - Invalid Start Date
**Expected Result:** Rejected

## RDG-022 - Invalid End Date
**Expected Result:** Rejected

## RDG-023 - Invalid format / separator
**Expected Result:** Rejected

## RDG-024 - Invalid time values
**Expected Result:** Rejected

---

# Copy Functionality

## RDG-025 - Copy output
**Expected Result:** Clipboard matches UI

## RDG-026 - Copy after regeneration
**Expected Result:** Latest output copied

---

# Download Functionality

## RDG-027 - Download file
**Expected Result:** File downloaded

## RDG-028 - Download content validation
**Expected Result:** Matches UI output

## RDG-029 - Multiple downloads
**Expected Result:** Works consistently

---

# UI & Stability

## RDG-030 - Stability under repeated usage
**Expected Result:** No crash

## RDG-031 - Format consistency after changes
**Expected Result:** Correct output always

## RDG-032 - Mixed separator handling
**Expected Result:** Rejected

## RDG-033 - Invalid custom tokens
**Expected Result:** Handled gracefully

## RDG-034 - Special characters in custom format
**Expected Result:** Literals preserved

## RDG-035 - Range validation consistency
**Expected Result:** Dates within range

## RDG-036 - Copy without regeneration
**Expected Result:** Works correctly

## RDG-037 - Download without regeneration
**Expected Result:** Works correctly

## RDG-038 - Settings change consistency
**Expected Result:** Output updates correctly

## RDG-039 - Exploratory stability checks
**Expected Result:** No unexpected behavior

---

## RDG-040 - Exploratory Testing (Full Flow Validation)

**Priority:** Medium

**Test Steps**
1. Randomly combine:
   - different number inputs
   - different formats
   - start/end date variations
2. Repeatedly generate, copy, download
3. Switch settings rapidly

**Expected Result**
- Application remains stable under unpredictable usage
- No crashes, freezes, or inconsistent outputs