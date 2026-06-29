# Test Cases - Random Date Generator

## Overview
Manual test cases for Random Date Generator validation.

https://codebeautify.org/generate-random-date

---

## Testing Types
- Functional Testing
- Boundary Value Analysis
- Negative Testing
- Exploratory Testing
- UI Validation
- Usability Testing

---

# 1. Functional Tests

## RDG-001 - Verify default page load behavior
Priority: High

**Preconditions:** User opens application

**Steps:**
1. Open Random Date Generator page
2. Observe default state

**Expected Result:**
- Page loads successfully
- Default values are displayed:
  - Number of dates = 10
  - Default format selected
  - Start/End dates populated
- 10 generated dates are visible

---

## RDG-002 - Verify Generate button functionality
Priority: High

**Steps:**
1. Observe current output
2. Click "Generate Random Date"

**Expected Result:**
- New random dates are generated
- Previous output is replaced

---

## RDG-003 - Verify auto update on configuration change
Priority: Medium

**Steps:**
1. Change number of dates
2. Change format
3. Change start/end date

**Expected Result:**
- Output updates automatically based on new configuration

---

# 2. Boundary & Input Validation

## RDG-004 - Generate minimum value (1)
Expected Result: 1 date generated

## RDG-005 - Generate standard value (10)
Expected Result: 10 dates generated

## RDG-006 - Zero input validation
Expected Result: Input is rejected or default value applied

## RDG-007 - Negative input validation
Expected Result: Input is rejected with validation message

## RDG-008 - Decimal input validation
Expected Result: Input is rejected OR clearly defined rounding behavior is displayed

## RDG-009 - Large input (9999)
Expected Result: System should prevent crash and enforce limit

## RDG-010 - Non-numeric input
Expected Result: Only numeric input is accepted

## RDG-011 - Empty input
Expected Result: Default value is restored or validation error shown

---

# 3. Date Format Tests

## RDG-012 - ISO 8601 format validation
Expected Result: Correct ISO format is generated

## RDG-013 - Standard format validation
Expected Result: Matches selected format exactly

## RDG-014 - Custom format validation
Expected Result: Tokens and literals are correctly applied

## RDG-015 - Custom format case sensitivity
Expected Result: System handles format consistently or defined behavior is applied

---

# 4. Start & End Date Tests

## RDG-016 - Valid date range
Expected Result: Generated dates are within range

## RDG-017 - Start equals End
Expected Result: Single exact date generated

## RDG-018 - Start greater than End
Expected Result: Validation error prevents generation

## RDG-019 - Invalid Start/End date
Expected Result: Invalid input is rejected

---

# 5. Copy Functionality

## RDG-020 - Copy output
Expected Result: Clipboard matches displayed output

## RDG-021 - Copy after regeneration
Expected Result: Latest output is copied

---

# 6. Download Functionality

## RDG-022 - Download file
Expected Result: File is downloaded successfully

## RDG-023 - Download content validation
Expected Result: Downloaded file matches UI output

---

# 7. UI & Stability

## RDG-024 - Stability under repeated actions
Expected Result: No crash or freeze occurs

## RDG-025 - Rapid configuration changes
Expected Result: System remains stable and consistent

## RDG-026 - Exploratory full flow testing
Expected Result: No unexpected behavior under mixed usage
