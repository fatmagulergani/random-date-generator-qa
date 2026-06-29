# Bug Report - Random Date Generator

## Overview
This document contains confirmed issues found during manual testing of the Random Date Generator tool.

---

# BUG-001 - Application crashes with Out of Memory error when large input is used

**Severity:** Critical  
**Priority:** High  
**Component:** Number of Dates Input  

## Description
When a very large number (e.g. 9999) is entered, the application becomes unresponsive and eventually crashes due to memory exhaustion.

## Steps to Reproduce
1. Open the Random Date Generator page  
2. Enter `9999` in "How many dates to generate?" field  
3. Click "Generate Random Date"

## Actual Result
- Browser becomes unresponsive  
- "Page Unresponsive" warning appears  
- "Aw, Snap! Out of Memory" crash occurs  

## Expected Result
- System should restrict maximum input value OR show validation error before processing  

## Impact
- Application crash  
- Poor performance handling  
- Potential denial-of-service scenario under extreme input  

---

# BUG-002 - Decimal input is accepted and rounded up without user notification

**Severity:** High  
**Priority:** High  
**Component:** Number of Dates Input  

## Description
Decimal values are accepted and automatically rounded up without user notification.

## Steps to Reproduce
1. Enter `1.5`  
2. Click Generate  
3. Observe output count  

## Actual Result
- `1.5 → 2` dates generated  
- `2.5 → 3` dates generated  
- No validation or explanation provided  

## Expected Result
- Decimal values should be rejected OR rounding behavior should be explicitly communicated  

## Impact
- Non-transparent input handling  
- User confusion  
- Inconsistent numeric validation behavior  

---

# BUG-003 - Inconsistent validation of invalid calendar dates

**Severity:** High  
**Priority:** High  
**Component:** Start Date / End Date Validation  

## Description
Invalid calendar dates are handled inconsistently. Some invalid inputs are rejected, while others are automatically normalized without user notification.

## Test Data
- `2020-12-32` → rejected  
- `2020-04-31` → accepted and normalized  
- `2020-02-30` → accepted and normalized  

## Actual Result
- Partial validation applied inconsistently  
- Some invalid dates are converted to valid ones without warning  

## Expected Result
- All invalid calendar dates should be consistently rejected OR normalization rules should be explicitly defined  

## Impact
- Data integrity issues  
- Inconsistent parsing behavior  
- Hidden data transformation  

---

# BUG-004 - Start Date greater than End Date still generates results

**Severity:** High  
**Priority:** High  
**Component:** Date Range Validation  

## Description
System allows Start Date to be greater than End Date and still generates results.

## Steps to Reproduce
1. Set Start Date: `9020-01-01`  
2. Set End Date: `2020-01-01`  
3. Click Generate  

## Actual Result
- Random dates are generated despite invalid range  

## Expected Result
- Validation error should prevent generation  

## Impact
- Logical inconsistency  
- Broken range validation  

---

# BUG-005 - Inconsistent handling of invalid date separators

**Severity:** Medium  
**Priority:** Low  
**Component:** Date Input Validation  

## Description
During testing, inconsistent behavior was observed when using unsupported date separators such as `/` or `*`.

This behavior was not consistently reproducible across all attempts, suggesting conditional validation behavior or input normalization differences.

## Steps Attempted
1. Enter `2222/02/29`
2. Enter `2223*03*29`
3. Click Generate

## Observed Behavior (intermittent)
- In some cases, input appears to be accepted and processed  
- In other attempts, behavior differs or is normalized/rejected  

## Expected Result
- System should consistently reject unsupported date formats OR clearly define supported formats  

## Impact
- Potential inconsistency in input validation logic  
- Confusing user experience  
- Risk of unpredictable parsing behavior  

## Notes
This issue could not be consistently reproduced and may require further investigation.

---

# BUG-006 - Duplicate format mapping for different output options

**Severity:** Medium  
**Priority:** High  
**Component:** Date Output Format  

## Description
Two different format options produce identical output, indicating incorrect format mapping.

## Steps to Reproduce
1. Select "Year Month Date hh:mm:ss"  
2. Generate dates  
3. Select "Year Date Month hh:mm:ss"  
4. Generate dates  
5. Compare outputs  

## Actual Result
- Both formats produce identical output  

## Expected Result
- Each format option should produce distinct mapped output  

## Impact
- Broken format configuration logic  
- User confusion  
- Incorrect mapping in format engine  

---

# BUG-007 - Download button allows unlimited duplicate file downloads

**Severity:** Medium  
**Priority:** Medium  
**Component:** Download Feature  

## Description
Users can repeatedly download identical files without restriction.

## Steps to Reproduce
1. Generate dates  
2. Click Download multiple times  

## Actual Result
- Unlimited identical downloads occur  

## Expected Result
- System should prevent redundant downloads OR indicate unchanged content  

## Impact
- Redundant file creation  
- Minor performance and storage inefficiency  

---

# BUG-008 - Ambiguous format label "Year Month Date"

**Severity:** Low  
**Priority:** Medium  
**Component:** Date Output Format UI  

## Description
The label "Year Month Date" is ambiguous and may confuse users.

The term "Date" is unclear and likely intended to represent "Day".

## Actual Result
- Label may cause interpretation confusion  

## Expected Result
- Clear naming such as "Year Month Day"  

## Impact
- UX confusion  
- Misinterpretation of format structure  