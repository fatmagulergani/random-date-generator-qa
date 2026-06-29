# Random Date Generator - QA Testing Project

## 📌 Overview
This project contains manual QA testing artifacts for the Random Date Generator tool:

https://codebeautify.org/generate-random-date

The goal of this QA effort is to evaluate:
- Functional correctness
- Input validation
- Boundary conditions
- UI behavior
- Data integrity
- System stability

---

## 🧪 Testing Scope

### Included
- Number of dates generation logic
- Date format selection
- Custom date format handling
- Start / End date validation
- Copy & Download functionality
- Edge cases & invalid inputs

### Excluded
- Backend/API implementation
- Infrastructure testing
- Third-party library internals
- Authentication / user management

---

## 🧠 Testing Approach

- Functional Testing
- Boundary Value Analysis
- Negative Testing
- Exploratory Testing
- UI/UX Validation
- Data Integrity Testing

---

## 🚨 Key Issues Found

### 🔴 Critical
- Application crash (Out of Memory) when large input (9999) is used

### 🔴 High Severity
- Decimal input accepted with implicit rounding
- Inconsistent invalid date validation behavior
- Start date greater than end date still generates results
- Invalid date formats accepted without proper validation

### 🟡 Medium Severity
- Duplicate format mapping issue in output formats
- Custom format case sensitivity issue
- Download allows unlimited duplicate downloads

### 🟢 Low Severity
- Ambiguous format labeling ("Year Month Date")

---

## 📸 Evidence / Screenshots

All bug evidence screenshots are located here:
ManualTesting/Screenshots/
Each bug in BugReport.md includes direct image references.

---

## 🐞 Bug Report
All detailed issues are documented in:
👉 `BugReport.md`

---

## 📊 Overall Assessment

The application demonstrates basic functionality but has several quality issues:

- Weak input validation layer
- Inconsistent date parsing logic
- Missing constraints for extreme inputs
- UX clarity issues in format naming

---

## 💡 Recommendations

- Implement strict input validation (numeric + date fields)
- Define consistent date parsing rules
- Add maximum limit for number generation
- Handle invalid calendar dates explicitly
- Improve format naming consistency and documentation

---

## 👩‍💻 Author Notes
This QA exercise was completed using:
- Manual exploratory testing
- Edge case analysis
- Functional verification
- Input validation testing
