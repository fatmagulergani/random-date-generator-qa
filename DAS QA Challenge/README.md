# Random Date Generator - QA Testing Project

## 📌 Overview
This project contains manual QA testing artifacts for the Random Date Generator tool.

https://codebeautify.org/generate-random-date

The purpose of this QA effort is to validate:
- Functional correctness
- Input validation
- Boundary conditions
- UI behavior
- Data integrity
- System stability

---

## 🧪 Testing Scope

### In Scope
- Random date generation logic
- Output display validation
- Copy & Download functionality
- Number of dates input validation
- Date format selection
- Custom format handling
- Start / End date logic

### Out of Scope
- Backend implementation
- External APIs / third-party internal logic
- Authentication / user management
- Infrastructure / performance testing (load testing)

---

## 🧠 Testing Approach
- Functional Testing
- Boundary Value Analysis
- Negative Testing
- Exploratory Testing
- UI/UX Validation
- Data Integrity Testing

---

## 🚨 Key Defects Summary

### 🔴 Critical
- Application crashes (Out of Memory) when large input (e.g., 9999) is used

### 🔴 High Severity
- Decimal input accepted and automatically rounded without user notification
- Inconsistent invalid date validation behavior
- Start Date greater than End Date still generates results
- Invalid calendar dates partially normalized without consistency

### 🟡 Medium Severity
- Duplicate format mapping for different output options
- Custom format case sensitivity inconsistency
- Repeated download allowed without restriction

### 🟢 Low Severity
- Ambiguous format label ("Year Month Date")

---

## 🐞 Bug Reports
All detailed defects are documented in:
👉 BugReport.md

Each bug includes:
- Steps to reproduce
- Actual vs expected results
- Severity & priority
- Evidence references

---

## 📸 Evidence
All screenshots are stored under:
ManualTesting/Screenshots/

Each bug is linked to its corresponding evidence in BugReport.md.

---

## 📊 Summary
The application demonstrates core functionality but shows several quality issues:

- Weak input validation
- Inconsistent date parsing logic
- Missing constraints for extreme inputs
- UX clarity issues in format naming

---

## 💡 Recommendations
- Implement strict input validation rules
- Define consistent date parsing behavior
- Add maximum input limits
- Standardize format naming conventions
- Improve error messaging clarity

---

## 👩‍💻 Author Notes
Testing was performed using:
- Manual exploratory testing
- Boundary analysis
- Negative testing techniques
- Functional verification
