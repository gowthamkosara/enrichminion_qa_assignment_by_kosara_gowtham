# Bug Reporting Guide – EnrichMinion QA Assignment

This document explains how to log, track, and analyze bugs discovered during manual testing of the **EnrichMinion Website**.

---

## File Included
Detailed bug log containing:
  - Bug ID  
  - Title / Description  
  - Severity / Priority  
  - Steps to Reproduce  
  - Expected Result  
  - Actual Result  
  - Evidence (screenshots or console logs)  
  - Root Cause Analysis (Frontend / Backend / Both)  

---

## Bug Report Format

| Field | Description |
|--------|-------------|
| **Bug ID** | Unique identifier (e.g., `BUG-UI-001` or `BUG-API-002`). |
| **Title** | Short summary of the issue. |
| **Module** | Signup / Login / Enrichment / Verification. |
| **Severity** | Critical / Major / Minor. |
| **Priority** | High / Medium / Low (based on business impact). |
| **Environment** | Browser, device, API environment (production / staging). |
| **Preconditions** | Setup required before reproducing (e.g., must be logged in). |
| **Steps to Reproduce** | Step-by-step actions to trigger the bug. |
| **Expected Result** | How the system should behave. |
| **Actual Result** | What actually happens (include error messages). |
| **Root Cause Analysis** | Identify whether issue originates in the frontend (UI/validation/rendering) or backend (API/data logic). Include reasoning. |
| **Status** | New / Open / Fixed / Retest / Closed. |

---

## Example Entry

### BUG-UI-001 | Signup allows invalid email format
- **Module:** Signup  
- **Severity:** Major  
- **Priority:** High  
- **Environment:** Chrome 129.0 / Windows 11  
- **Preconditions:** User not logged in  
- **Steps to Reproduce:**
  1. Navigate to signup page.  
  2. Enter `test@.com` in the email field and a valid password.  
  3. Click on **Sign Up**.  
- **Expected Result:** Validation error should display “Enter a valid email.”  
- **Actual Result:** User is registered successfully.   
- **Root Cause Analysis:** **Frontend issue** – missing email format validation before API call.  
- **Status:** Open  

---

### BUG-API-002 | Login returns 500 Internal Server Error for invalid payload
- **Module:** Login API  
- **Severity:** Critical  
- **Priority:** High  
- **Environment:** Postman / Live endpoint  
- **Preconditions:** None  
- **Steps to Reproduce:**
  1. Send POST `/api/auth/login` with malformed JSON (`{"email":"test@example.com","password":}`)  
  2. Observe the server response.  
- **Expected Result:** Server should return `400 Bad Request` with a clear message like “Invalid JSON format.”  
- **Actual Result:** Server returns `500 Internal Server Error`.    
- **Root Cause Analysis:** **Backend issue** – improper request body validation and error handling.  
- **Status:** New  

---

##  Root Cause Categories
| Area | Description | Examples |
|------|--------------|----------|
| **Frontend** | Issues with form validation, navigation, or display. | Wrong error message, misaligned button, missing input validation. |
| **Backend** | Server-side data validation, response schema, or logic issues. | Wrong status codes, incorrect API responses, DB errors. |
| **Both** | UI and API behave inconsistently together. | UI accepts invalid input, API also stores it incorrectly. |

---

## Reporting Tips
- Always check **console logs** and **network tab** before deciding root cause.  
- Include **timestamps** or **session details** if issue occurs intermittently.  
- Prioritize issues that **block core functionality** (Signup, Login, Enrichment).  

---

## Suggested Folder Structure

```
enrichminion_qa_assignment/
├── ui_test_cases.xlsx
├── api_test_cases.xlsx
├── bug_report.md
```
---

**Author:** Gowtham Kosara  
**Project:** EnrichMinion QA Assignment  
**Date:** 2025-11-04

---