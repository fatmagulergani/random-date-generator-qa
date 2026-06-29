# Test Cases - Random Date Generator

## Overview

Manual test cases for Random Date Generator validation.  
**URL:** https://codebeautify.org/generate-random-date  
**Tester:** Fatma Gül Ergani  
**Date Executed:** June 2026  
**Browser:** Google Chrome | **OS:** Windows 10

---

## Test Execution Summary

| Total | Pass | Fail |
|-------|------|------|
| 28    | 20   | 8    |

---

## 1. Functional Tests

### RDG-001 - Verify default page load behavior

**Priority:** High  
**Preconditions:** User has a browser open and navigates to the application URL.

**Steps:**
1. Open the Random Date Generator page.
2. Observe the default state of all input fields and the output area.

**Expected Result:**
- Page loads successfully without errors.
- Default values are displayed: Number of dates = 10, a default format is selected, Start and End dates are pre-populated.
- 10 generated dates are visible in the output area.

**Actual Result:** Page loaded successfully. Default values were displayed as expected. 10 dates were pre-generated on load.  
**Status:** ✅ Pass

---

### RDG-002 - Verify Generate button functionality

**Priority:** High  
**Preconditions:** Application is loaded with default configuration.

**Steps:**
1. Note the current output displayed on the page.
2. Click the "Generate Random Date" button.

**Expected Result:**
- New random dates are generated.
- Previous output is replaced with new results.

**Actual Result:** Clicking the button generated a new set of dates and replaced the previous output as expected.  
**Status:** ✅ Pass

---

### RDG-003 - Verify auto update on configuration change

**Priority:** Medium  
**Preconditions:** Application is loaded with default configuration.

**Steps:**
1. Change the number of dates input field to a different value.
2. Change the selected date format.
3. Change the Start and End date values.

**Expected Result:**
- Output updates automatically to reflect the new configuration without requiring a manual generate action.

**Actual Result:** Output updated automatically upon configuration changes as expected.  
**Status:** ✅ Pass

---

## 2. Boundary & Input Validation

### RDG-004 - Generate minimum value (1)

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Clear the number of dates input field.
2. Enter the value `1`.
3. Click "Generate Random Date".

**Expected Result:**
- Exactly 1 date is generated and displayed in the output area.

**Actual Result:** Exactly 1 date was generated and displayed correctly.  
**Status:** ✅ Pass

---

### RDG-005 - Generate standard value (10)

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Clear the number of dates input field.
2. Enter the value `10`.
3. Click "Generate Random Date".

**Expected Result:**
- Exactly 10 dates are generated and displayed in the output area.

**Actual Result:** Exactly 10 dates were generated and displayed correctly.  
**Status:** ✅ Pass

---

### RDG-006 - Zero input validation

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Clear the number of dates input field.
2. Enter the value `0`.
3. Click "Generate Random Date".

**Expected Result:**
- Input is rejected with a validation message, OR the field reverts to a default value.
- No output is generated for a zero input.

**Actual Result:** Zero input was handled gracefully; no dates were generated and the application remained stable.  
**Status:** ✅ Pass

---

### RDG-007 - Negative input validation

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Clear the number of dates input field.
2. Enter the value `-5`.
3. Click "Generate Random Date".

**Expected Result:**
- Input is rejected with a clear validation message.
- No output is generated for a negative input.

**Actual Result:** Negative input was rejected and no dates were generated.  
**Status:** ✅ Pass

---

### RDG-008 - Decimal input validation

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Clear the number of dates input field.
2. Enter the value `1.5`.
3. Click "Generate Random Date".
4. Repeat with value `2.5`.

**Expected Result:**
- Decimal input is rejected with a validation message, OR rounding behavior is clearly communicated to the user.

**Actual Result:** Decimal values were silently rounded (e.g., 1.5 → 2) without any user notification or validation message. See BUG-002.  
**Status:** ❌ Fail — See [BUG-002]

---

### RDG-009 - Large input (9999)

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Clear the number of dates input field.
2. Enter the value `9999`.
3. Click "Generate Random Date".

**Expected Result:**
- System prevents processing of extreme values by enforcing a maximum input limit.
- Browser does not crash or become unresponsive.

**Actual Result:** Browser became unresponsive and an "Out of Memory" error occurred. Application crashed. See BUG-001.  
**Status:** ❌ Fail — See [BUG-001]

---

### RDG-010 - Non-numeric input

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Click on the number of dates input field.
2. Type alphabetical characters, e.g., `abc`.
3. Click "Generate Random Date".

**Expected Result:**
- Non-numeric input is rejected or not accepted by the field.

**Actual Result:** Non-numeric characters were not accepted by the field; input was handled correctly.  
**Status:** ✅ Pass

---

### RDG-011 - Empty input

**Priority:** Medium  
**Preconditions:** Application is loaded.

**Steps:**
1. Clear the number of dates input field completely.
2. Click "Generate Random Date".

**Expected Result:**
- The field reverts to a default value, OR a validation error is displayed.

**Actual Result:** Empty input was handled without errors; application remained stable.  
**Status:** ✅ Pass

---

## 3. Date Format Tests

### RDG-012 - ISO 8601 format validation

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Select "ISO 8601" from the date format dropdown.
2. Click "Generate Random Date".

**Expected Result:**
- All generated dates conform to the ISO 8601 standard format.

**Actual Result:** Generated dates conformed to ISO 8601 format as expected.  
**Status:** ✅ Pass

---

### RDG-013 - Standard format validation

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Select a standard format from the dropdown (e.g., `MM-DD-YYYY`).
2. Click "Generate Random Date".
3. Verify each generated date matches the selected format exactly.

**Expected Result:**
- All generated dates match the selected format with correct separators and field order.

**Actual Result:** Some format options produced identical output despite having different labels. See BUG-006.  
**Status:** ❌ Fail — See [BUG-006]

---

### RDG-014 - Custom format validation

**Priority:** Medium  
**Preconditions:** Application is loaded.

**Steps:**
1. Select "Custom date format" from the dropdown.
2. Enter a custom format string, e.g., `DD/MM/YYYY`.
3. Click "Generate Random Date".

**Expected Result:**
- Tokens are correctly substituted and literal characters are preserved.

**Actual Result:** Custom format tokens were applied correctly for standard inputs.  
**Status:** ✅ Pass

---

### RDG-015 - Custom format case sensitivity

**Priority:** Medium  
**Preconditions:** Application is loaded with "Custom date format" selected.

**Steps:**
1. Enter a format using lowercase tokens, e.g., `dd/mm/yyyy`.
2. Click "Generate Random Date".
3. Repeat using uppercase tokens, e.g., `DD/MM/YYYY`.

**Expected Result:**
- The system applies consistent behavior for both cases.

**Actual Result:** System documentation specifies which tokens are supported (uppercase only). Behavior was consistent with the documented specification. No issue observed.  
**Status:** ✅ Pass

---

## 4. Start & End Date Tests

### RDG-016 - Valid date range

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Set Start date to `01/01/2000`.
2. Set End date to `12/31/2020`.
3. Click "Generate Random Date".

**Expected Result:**
- All generated dates fall within the specified range (inclusive).

**Actual Result:** All generated dates fell within the specified range as expected.  
**Status:** ✅ Pass

---

### RDG-017 - Start equals End date

**Priority:** Medium  
**Preconditions:** Application is loaded.

**Steps:**
1. Set Start date to `06/15/2023`.
2. Set End date to `06/15/2023`.
3. Set number of dates to `5`.
4. Click "Generate Random Date".

**Expected Result:**
- All generated dates are exactly `06/15/2023`.

**Actual Result:** All generated dates matched the single specified date as expected.  
**Status:** ✅ Pass

---

### RDG-018 - Start Date greater than End Date

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Set Start date to `01/01/2025`.
2. Set End date to `01/01/2020`.
3. Click "Generate Random Date".

**Expected Result:**
- A validation error is displayed; no dates are generated.

**Actual Result:** Dates were still generated despite Start date being later than End date. No validation error was shown. See BUG-004.  
**Status:** ❌ Fail — See [BUG-004]

---

### RDG-019 - Invalid Start/End date

**Priority:** High  
**Preconditions:** Application is loaded.

**Steps:**
1. Enter an invalid value in the Start date field, e.g., `13/40/2023`.
2. Click "Generate Random Date".
3. Repeat with an invalid End date.

**Expected Result:**
- Invalid date input is rejected with a clear validation message.

**Actual Result:** Behavior was inconsistent — some invalid dates were rejected while others were silently normalized (e.g., April 31 → May 1). See BUG-003.  
**Status:** ❌ Fail — See [BUG-003]

---

### RDG-028 - Start and End date input with different formats

**Priority:** Medium  
**Preconditions:** Application is loaded.

**Steps:**
1. Enter Start date using different separators, e.g., `01-01-2000`, `01/01/2000`, `01.01.2000`.
2. Enter End date using a different format than the Start date, e.g., Start: `01/01/2000`, End: `31-12-2020`.
3. Click "Generate Random Date" after each variation.
4. Observe how the system handles each format combination.

**Expected Result:**
- System either accepts a single consistent format and rejects others with a clear message, OR normalizes all variations consistently.
- Behavior is predictable and documented.

**Actual Result:** Inconsistent behavior observed — different separators and format variations were handled differently depending on the input combination, without clear validation rules or user feedback. See BUG-005.  
**Status:** ❌ Fail — See [BUG-005]

---

## 5. Copy Functionality

### RDG-020 - Copy output

**Priority:** Medium  
**Preconditions:** At least one date has been generated.

**Steps:**
1. Click the "Copy" button.
2. Paste the clipboard content into a text editor.

**Expected Result:**
- Clipboard content matches exactly what is displayed in the output area.

**Actual Result:** Copied content matched the displayed output exactly.  
**Status:** ✅ Pass

---

### RDG-021 - Copy after regeneration

**Priority:** Medium  
**Preconditions:** Dates have been generated at least once.

**Steps:**
1. Generate a set of dates and note the output.
2. Click "Generate Random Date" again to produce new output.
3. Click the "Copy" button and paste into a text editor.

**Expected Result:**
- The copied content reflects the latest generated output.

**Actual Result:** Latest output was copied correctly after regeneration.  
**Status:** ✅ Pass

---

## 6. Download Functionality

### RDG-022 - Download file

**Priority:** Medium  
**Preconditions:** At least one date has been generated.

**Steps:**
1. Click the "Download" button.

**Expected Result:**
- A file is downloaded successfully to the local system.

**Actual Result:** File was downloaded successfully. However, repeated downloads could be triggered without restriction. See BUG-007.  
**Status:** ❌ Fail — See [BUG-007]

---

### RDG-023 - Download content validation

**Priority:** Medium  
**Preconditions:** A file has been downloaded.

**Steps:**
1. Generate dates and click "Download".
2. Open the downloaded file and compare with UI output.

**Expected Result:**
- Downloaded file content matches the output displayed in the UI.

**Actual Result:** Downloaded file content matched the UI output correctly.  
**Status:** ✅ Pass

---

## 7. UI & Stability

### RDG-024 - Stability under repeated actions

**Priority:** Medium  
**Preconditions:** Application is loaded.

**Steps:**
1. Click "Generate Random Date" 20 times in succession.
2. Observe browser and application behavior throughout.

**Expected Result:**
- Application remains stable and responsive throughout.

**Actual Result:** Application remained stable under repeated generate actions with normal input values.  
**Status:** ✅ Pass

---

### RDG-025 - Rapid configuration changes

**Priority:** Medium  
**Preconditions:** Application is loaded.

**Steps:**
1. Rapidly change the date format, number of dates, and date range multiple times.
2. Click "Generate Random Date" after each change.

**Expected Result:**
- System handles rapid input changes gracefully and output reflects the most recent configuration.

**Actual Result:** Application handled rapid configuration changes without crashing or producing inconsistent output.  
**Status:** ✅ Pass

---

### RDG-026 - Exploratory full flow testing

**Priority:** Low  
**Preconditions:** Application is loaded.

**Steps:**
1. Perform a full end-to-end flow: set all parameters, generate dates, copy output, and download file.
2. Mix valid and boundary inputs across multiple sessions.
3. Observe any unexpected behaviors not covered by previous test cases.

**Expected Result:**
- No unexpected behavior, UI glitches, or errors occur during mixed usage.

**Actual Result:** Overall flow functioned as expected. Issues noted in individual test cases above. Format label "Year Month Date" observed to use incorrect terminology — "Date" should read "Day". See BUG-008.  
**Status:** ❌ Fail — See [BUG-008]

---

### RDG-027 - Cross-browser and cross-device compatibility

**Priority:** Medium  
**Preconditions:** Application is accessible on multiple browsers and/or devices.

**Steps:**
1. Open the application on Microsoft Edge (Windows 10).
2. Perform a basic flow: generate dates with default settings, copy output, download file.
3. Repeat the same flow on additional browsers (e.g., Firefox, Safari) if available.
4. Repeat on a mobile device if available (e.g., Android or iOS browser).

**Expected Result:**
- Application renders correctly and all core features (generate, copy, download) function consistently across all tested browsers and devices.
- No layout issues, broken elements, or functional differences between environments.

**Actual Result:** Tested on Microsoft Edge (Windows 10) — core functionality worked correctly, no layout or functional issues observed. Testing on additional browsers (Firefox, Safari) and mobile devices is recommended for full compatibility coverage.  
**Status:** ✅ Pass (Edge) — Further testing recommended on Firefox, Safari, and mobile devices
