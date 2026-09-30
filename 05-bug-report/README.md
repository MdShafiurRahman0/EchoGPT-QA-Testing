# Bug Report — EchoGPT

[← Back to main report](../README.md)

[![Google Sheet](https://img.shields.io/badge/Bug%20Report-Google%20Sheet-34A853?logo=googlesheets&logoColor=white)](https://docs.google.com/spreadsheets/d/1p3WAoCSoEeSj-DAn9NIDAlIAci20hGPBC4KySS26HcI/edit?usp=sharing)

## Overview

| Field | Details |
|---|---|
| **Application** | EchoGPT (Chrome extension and Android app) |
| **Bugs reported** | 7 (BUG-001 to BUG-007) |
| **Platforms** | Chrome Extension (4 bugs), Android App (3 bugs) |
| **Tested by** | Md. Shafiur Rahman |

## Summary

### By severity

| Severity | Count |
|---|:---:|
| 🔴 Critical | 0 |
| 🟠 High | 3 |
| 🟡 Medium | 4 |
| 🟢 Low | 0 |
| **Total** | **7** |

### By priority

| Priority | Count |
|---|:---:|
| High | 5 |
| Medium | 2 |
| Low | 0 |
| **Total** | **7** |

### By area

| Area | Bugs | IDs |
|---|:---:|---|
| Payment | 3 | BUG-003, BUG-004, BUG-007 |
| Chat | 2 | BUG-005, BUG-006 |
| Account / Authentication | 1 | BUG-001 |
| Compare | 1 | BUG-002 |

## All Bugs at a Glance

| ID | Platform | Title | Severity | Priority |
|---|---|---|---|---|
| BUG-001 | Chrome Extension | Incorrect validation message on Create Account screen | 🟡 Medium | High |
| BUG-002 | Chrome Extension | Compare with feature does not generate a comparison response | 🟡 Medium | Medium |
| BUG-003 | Chrome Extension | Payment modal overlaps with subscription page, causing a UI rendering glitch | 🟡 Medium | Medium |
| BUG-004 | Chrome Extension | Stripe payment cancel redirects to a 404 Not Found page | 🟠 High | High |
| BUG-005 | Android App | Single prompt is submitted twice | 🟡 Medium | High |
| BUG-006 | Android App | Conversation stays stuck on loading without generating a response | 🟠 High | High |
| BUG-007 | Android App | BDT payment initiation fails with an SSL configuration error | 🟠 High | High |

## Detailed Bug Reports

### Account / Authentication

<details>
<summary><b>BUG-001</b> — Incorrect validation message on Create Account screen &nbsp; 🟡 Medium</summary>

| Field | Details |
|---|---|
| **Platform** | Chrome Extension |
| **Environment** | EchoGPT Chrome extension installed in Brave Browser on Linux |
| **Severity / Priority** | Medium / High |
| **Related** | TC-03, ET-03 |

**Description:** On the Create Account screen only the Email Address field is visible. After clicking Send Verification Code, the system shows "First name is required" even though there is no First Name field.

**Steps to Reproduce**
1. Open the EchoGPT Chrome extension in the browser sidebar.
2. Click Create New Account.
3. Enter a valid email address.
4. Click Send Verification Code.

**Expected Result:** The system validates the email field or shows an error relevant to the visible form fields.

**Actual Result:** The system shows "First name is required" although no First Name field exists on the screen.

</details>

### Compare

<details>
<summary><b>BUG-002</b> — Compare with feature does not generate a comparison response &nbsp; 🟡 Medium</summary>

| Field | Details |
|---|---|
| **Platform** | Chrome Extension |
| **Environment** | EchoGPT Chrome extension, Google Chrome (latest), Linux (Deepin 25) |
| **Severity / Priority** | Medium / Medium |

**Description:** The Compare with section lets the user select another AI model, but no comparison output is generated. The model selector at the bottom of EchoGPT works correctly.

**Steps to Reproduce**
1. Open an existing chat.
2. Click Compare and select a model.
3. Wait for the comparison result.

**Expected Result:** A comparison response is generated using the selected model.

**Actual Result:** No comparison response is displayed after selecting the model.

</details>

### Payment

<details>
<summary><b>BUG-004</b> — Stripe payment cancel redirects to a 404 Not Found page &nbsp; 🟠 High</summary>

| Field | Details |
|---|---|
| **Platform** | Chrome Extension |
| **Environment** | EchoGPT Chrome extension, Google Chrome (latest), Linux (Deepin 25) |
| **Severity / Priority** | High / High |

**Description:** When a user cancels the Stripe payment, the application redirects to a raw API endpoint that returns a 404 JSON response instead of returning the user to the website.

**Steps to Reproduce**
1. Log in to the EchoGPT extension.
2. Click Upgrade.
3. Select a plan.
4. Click International Payment.
5. Submit.
6. Select Online Payment.
7. Fill in the payment fields and click Cancel.

**Expected Result:** The user is redirected back to the checkout or order page with a friendly message such as "Payment cancelled".

**Actual Result:** The browser shows a JSON error page: `404 Not Found (Cannot GET /v1/api-invoice/stripe/cancel)`.

</details>

<details>
<summary><b>BUG-007</b> — BDT payment initiation fails with an SSL configuration error &nbsp; 🟠 High</summary>

| Field | Details |
|---|---|
| **Platform** | Android App |
| **Environment** | EchoGPT Android app (environment details not recorded in the sheet) |
| **Severity / Priority** | High / High |

**Description:** Selecting Pay in BDT fails to start the payment and shows a raw SSL / admin configuration error instead of a user-friendly payment failure message.

**Steps to Reproduce**
1. Open the EchoGPT Android app.
2. Go to Upgrade.
3. Select a premium plan.
4. Choose Pay in BDT.
5. Tap the payment button.

**Expected Result:** The BDT payment gateway initialises successfully, or a clear, user-friendly error message is shown.

**Actual Result:** The payment fails and the app shows: "SSL payment initiation failed: Transaction amount is not allowed as per admin configuration!"

</details>

<details>
<summary><b>BUG-003</b> — Payment modal overlaps with subscription page, causing a UI rendering glitch &nbsp; 🟡 Medium</summary>

| Field | Details |
|---|---|
| **Platform** | Chrome Extension |
| **Environment** | EchoGPT Chrome extension, Google Chrome (latest), Linux (Deepin 25) |
| **Severity / Priority** | Medium / Medium |
| **Screen recording** | [View on Google Drive](https://drive.google.com/file/d/1UPXvgCScwo6ddbMQGIPY1z3xfJ3EhjSv/view?usp=sharing) |

**Description:** When the user clicks Subscribe Now, the Choose Payment Method modal opens but overlaps the subscription plan card. Both layers stay visible, which makes the interface look broken and partly unreadable.

**Steps to Reproduce**
1. Open the EchoGPT extension.
2. Go to Upgrade.
3. Click Subscribe Now on any paid plan.

**Expected Result:** A centered payment modal opens with the background properly dimmed, and the subscription page does not overlap the modal.

**Actual Result:** The payment modal opens while the subscription card stays visible underneath, creating an overlapping, glitchy layout.

</details>

### Chat (Android)

<details>
<summary><b>BUG-006</b> — Conversation stays stuck on loading without generating a response &nbsp; 🟠 High</summary>

| Field | Details |
|---|---|
| **Platform** | Android App |
| **Environment** | EchoGPT Android app (environment details not recorded in the sheet) |
| **Severity / Priority** | High / High |

**Description:** After a prompt is sent, the conversation stays on "Loading conversation…" for a long time and no AI response is generated.

**Steps to Reproduce**
1. Open the EchoGPT Android app.
2. Enter a valid prompt, for example "write 1000 words SOP".
3. Tap Send once.
4. Wait for the response.

**Expected Result:** The loading indicator disappears and the AI returns a response within a reasonable time.

**Actual Result:** The app stays on "Loading conversation…" and no response is displayed.

</details>

<details>
<summary><b>BUG-005</b> — Single prompt is submitted twice &nbsp; 🟡 Medium</summary>

| Field | Details |
|---|---|
| **Platform** | Android App |
| **Environment** | EchoGPT Android app, Free account |
| **Severity / Priority** | Medium / High |

**Description:** When the user sends a prompt once, the same prompt appears twice in the conversation, even though Send was tapped only once.

**Steps to Reproduce**
1. Open the EchoGPT Android app.
2. Type a prompt, for example "Who are you, what can you do?".
3. Tap Send once.

**Expected Result:** The prompt appears only once in the conversation.

**Actual Result:** The same prompt is displayed twice in the chat history.

</details>

## Bug Report Template

| Column | Description |
|---|---|
| Bug ID | Unique ID (`BUG-001` and up) |
| Title | Short summary of the problem |
| Description | What the problem is and where it appears |
| Steps to Reproduce | Exact steps to trigger the bug |
| Expected Result | What should happen |
| Actual Result | What actually happens |
| Severity | Impact on the product (Critical / High / Medium / Low) |
| Priority | Urgency of the fix (High / Medium / Low) |
| Environment | Platform, browser or device used |
| Screenshot or Screen Recording | Evidence link |
