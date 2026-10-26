# Test Plan: ThreadPilot AI (Shopify App MVP)

## 1. Introduction & Scope
This document outlines the testing strategy for the ThreadPilot AI MVP based on the author's 3-day test plan. The goal is to verify the core functionality (OAuth, draft creation) and ensure the app operates in "Safe Mode" (no auto-publishing).

**Out of scope:** 
* Real financial transactions (payments, refunds).
* Ad spend verification.
* Live trend research.
* Automated Print-on-Demand fulfillment (not yet implemented in MVP).

## 2. Test Environment
*   **OS:** Ubuntu (Local run via `uvicorn`)
*   **Browser:** Google Chrome
*   **Shopify Store:** Shopify Development Store (created manually for testing)
*   **API Testing:** Local execution using sample data (without `AI_API_KEY`)

## 3. Test Approach (3-Day Plan Coverage)

### Install & Connect
*   **Setup:** Create a development store, deploy locally, configure `.env` keys.
*   **Testing:** Verify OAuth flow, domain validation (checking `.myshopify.com` requirement), and dashboard connection (verifying the correct store name is displayed).
*   **Status:** *Partially covered by test cases (TC-01 to TC-03).*

### Draft Workflow
*   **Testing:** Verify generation of ideas for US, UK, and AU markets. Create an unpublished product draft and verify that title, description, and tags match exactly in the Shopify Admin. 
*   **Manual Steps:** Add mockups, variants, and pricing manually in Shopify.
*   **Business Analysis:** Check print-on-demand costs and margins. 
*   **Status:** *Draft creation logic covered (TC-04, TC-05). Manual steps and margin checks require a separate checklist.*

### Safety & Review
*   **Testing:** Confirm no auto-publishing and no ad spend. Verify `draft_error` logging.
*   **Cleanup:** Remove test drafts, review activity logs.
*   **Status:** *Security logic covered (TC-06, TC-07). Cleanup and payment readiness require manual verification.*

## 4. Risks & Limitations
*   The app is an MVP. Features like AI image generation, live trends, and customer support are not implemented yet.
*   A 3-day test checks the workflow only; it does not guarantee actual sales. Real orders require working checkout and upfront cash for print providers.
