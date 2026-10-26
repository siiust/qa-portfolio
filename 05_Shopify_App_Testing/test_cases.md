# Test Cases for ThreadPilot AI (Shopify App MVP)

**Based on:** [Issue #1](https://github.com/herekhan927-sketch/Alitesting/issues/1)

## 1. Domain Validation Testing (From shopify_api.py)

| ID | Title | Steps | Expected Result | Status |
|---|---|---|---|---|
| TC-01 | Valid Shopify domain | 1. Open the main page. 2. Enter `test-store.myshopify.com`. 3. Click "Connect". | Redirect to Shopify authorization page (OAuth). | PASSED (locally) |
| TC-02 | Invalid domain (without .myshopify) | 1. Enter `test-store.com`. 2. Click "Connect". | Error 400: "Use your *.myshopify.com domain." | PASSED (locally) |
| TC-03 | Validation for empty field | 1. Leave the field empty. 2. Click "Connect". | Browser requires filling the field (HTML5 validation). | PASSED (locally) |

## 2. Draft Creation Logic Testing (From main.py, create_draft function)

**Precondition:** The app is installed and connected to a store.

| ID | Title | Steps | Expected Result |
|---|---|---|---|
| TC-04 | Create a draft with valid data | 1. Fill in Title, Description, Tags. 2. Click "Create draft". | Product is created with `draft` status. A message with the product ID appears. |
| TC-05 | Verify "draft" status | 1. Create a draft. 2. Go to Shopify admin. | Product is in the "Drafts" section, not published. |

## 3. Security Testing (From README and main.py)

| ID | Title | Expected Result |
|---|---|---|
| TC-06 | Check "Safe Mode" | In `main.py` (`create_draft` function), `"status":"draft"` is explicitly set. Automatic publishing is impossible. |
| TC-07 | Shopify API error handling | If the Shopify API is unavailable (e.g., invalid token), `draft_error` appears in the logs, and the user sees the message "Draft failed". |


Note: This is a preliminary draft based on code review. I used AI assistance to help structure the markdown tables and speed up the initial documentation process, but the test scenarios were derived from my own analysis of the provided source code.
