# Test Cases — ThreadPilot AI (Shopify App MVP)

**Reference:** [Issue #1](https://github.com/herekhan927-sketch/Alitesting/issues/1)

## 1. Shopify Domain Validation

| ID | Test Case | Steps | Expected Result | Status |
|---|---|---|---|---|
| TC-01 | Connect using a valid Shopify domain | 1. Open the app. 2. Enter `test-store.myshopify.com`. 3. Click **Connect**. | The app redirects to the Shopify authorization page. | Passed locally |
| TC-02 | Reject an invalid domain | 1. Enter `test-store.com`. 2. Click **Connect**. | The app rejects the domain and displays an appropriate validation error. | Passed locally |
| TC-03 | Submit an empty domain field | 1. Leave the domain field empty. 2. Click **Connect**. | The browser prevents form submission and requests a value. | Passed locally |

## 2. Draft Product Creation

**Precondition:** The app is installed and connected to a Shopify store.

| ID | Test Case | Steps | Expected Result | Status |
|---|---|---|---|---|
| TC-04 | Create a draft product | 1. Enter a title, description, and tags. 2. Click **Create draft**. | The product is created with draft status, and the app displays the product ID. | Not tested |
| TC-05 | Verify the product is not published | 1. Create a draft product. 2. Open Shopify admin. 3. Locate the product. | The product appears as a draft and is not published. | Not tested |

## 3. Error Handling and Safety Checks

| ID | Test Case | Steps | Expected Result | Status |
|---|---|---|---|---|
| TC-06 | Verify draft status in the creation logic | 1. Review the `create_draft` function in `main.py`. 2. Check the product status passed to the Shopify API. | The function explicitly sets the product status to `draft`. | Code reviewed |
| TC-07 | Handle a Shopify API error | 1. Simulate an API failure using a controlled test setup. 2. Attempt to create a draft. | The error is handled, relevant diagnostic information is logged, and the user receives an appropriate error message. | Not tested |

**Scope:** These test cases were prepared from a review of the available source code and project documentation. AI assistance was used to organize and edit the documentation.

