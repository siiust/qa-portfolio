# Bug Reports

## BUG-01: Lack of input length validation for the "Niche" field on the backend

**Project:** ThreadPilot AI (Shopify App MVP)
**Severity:** Minor 
**Priority:** Low

**Preconditions:** 
The app is installed, and the user is authorized in the Dashboard.

**Steps to reproduce:**
1. Open the Dashboard.
2. In the "Niche" input field, paste a string longer than 1000 characters.
3. Click the "Generate ideas" button.

**Expected result:** 
The system should return a clear validation error message (e.g., "Niche is too long. Maximum 100 characters allowed.") and prevent the request from being sent.

**Actual result:**
In the source code (`storage.py`, `log` function), the input is silently truncated to 1000 characters (`details[:1000]`). The user is not notified about the truncation, which can lead to unexpected behavior or data loss in the logs.

**Environment:** 
Local run (`uvicorn`), Browser: Google Chrome, OS: Ubuntu 26.04.01 LTS.

*Note: This issue was identified during static code review and can be verified via API testing.*
