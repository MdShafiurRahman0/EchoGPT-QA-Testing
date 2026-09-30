# 🤖 EchoGPT — QA Testing Report

![Functional Test Cases](https://img.shields.io/badge/Functional%20Test%20Cases-30-blue)
![Exploratory Sessions](https://img.shields.io/badge/Exploratory%20Sessions-26-purple)
![API Tests](https://img.shields.io/badge/API%20Tests-5%2F5%20Passed-brightgreen)
![UX Observations](https://img.shields.io/badge/UX%20Observations-10-orange)
![Bugs Reported](https://img.shields.io/badge/Bugs%20Reported-7-red)

A manual QA and API testing report for **EchoGPT**, a multi-model AI chat assistant available as a **Chrome extension** (browser sidebar) and an **Android app**. The work covers functional testing, exploratory testing, API testing with Postman, a UI/UX review and a consolidated bug report. Each activity is documented in its own folder and backed by a Google Sheet.

---

## Table of Contents

- [Testing Activities](#testing-activities)
- [Test Environment](#test-environment)
- [Results at a Glance](#results-at-a-glance)
- [Key Findings](#key-findings)
- [Tools and Techniques](#tools-and-techniques)
- [Repository Structure](#repository-structure)
- [Author](#author)

---

## Testing Activities

| # | Activity | What was covered | Documentation | Google Sheet |
|:-:|---|---|---|---|
| 1 | **Functional Testing** | 30 test cases across the Chrome extension and the Android app | [01-functional-testing](01-functional-testing/) | [Open Sheet](https://docs.google.com/spreadsheets/d/1FwJLr35Q-L4Uh9ePLh0ot-wjGpkEkUm4WYPQymxh424/edit?usp=sharing) |
| 2 | **Exploratory Testing** | 26 sessions with edge cases, observations and recommendations | [02-exploratory-testing](02-exploratory-testing/) | [Open Sheet](https://docs.google.com/spreadsheets/d/1zX9DCun1FpW0InNQmD-_IkQO32p0yvJJO9Di-ekcbFE/edit?usp=sharing) |
| 3 | **API Testing (Postman)** | 5 requests against the EchoGPT API | [03-api-testing-postman](03-api-testing-postman/) | [Open Sheet](https://docs.google.com/spreadsheets/d/10jK8ed27NgBHCfMcEajR1uUYRLy8fuhFOAXO8uqbwTs/edit?usp=sharing) |
| 4 | **UI/UX Review** | 10 interface observations with design recommendations | [04-ui-ux-review](04-ui-ux-review/) | [Open Sheet](https://docs.google.com/spreadsheets/d/1aYE7dZlFGglq2MiC3P0CGkayBfPWmMcB8noeB-u-njM/edit?usp=sharing) |
| 5 | **Bug Report** | 7 defects with steps, expected vs. actual result, severity and priority | [05-bug-report](05-bug-report/) | [Open Sheet](https://docs.google.com/spreadsheets/d/1p3WAoCSoEeSj-DAn9NIDAlIAci20hGPBC4KySS26HcI/edit?usp=sharing) |

---

## Test Environment

| Area | Environment |
|---|---|
| **Chrome Extension** | EchoGPT extension on Google Chrome (latest), Linux (Deepin 25). One bug was also observed in Brave Browser on Linux |
| **Android App** | EchoGPT Android app, Free account |
| **API** | Postman, using a Bearer token captured from the browser DevTools Network tab |
| **Account type** | Free plan (usage limit and paid-only features were part of the tests) |
| **Tested by** | Md. Shafiur Rahman |

---

## Results at a Glance

| Activity | Volume | Result |
|---|---|---|
| Functional Testing | 30 test cases (20 Extension, 10 Android) | 27 Pass, 2 Fail, 1 not recorded |
| Exploratory Testing | 26 sessions | 1 High, 5 Medium, 20 Low |
| API Testing | 5 requests (3 GET, 1 POST, 1 DELETE) | 5 Pass |
| UI/UX Review | 10 observations | Recommendations for every observation |
| Bug Report | 7 bugs | 3 High, 4 Medium |

---

## Key Findings

### Highest-severity bugs

| ID | Platform | Bug | Severity |
|---|---|---|---|
| **BUG-004** | Chrome Extension | Cancelling a Stripe payment lands on a raw 404 JSON page instead of returning the user to the app | 🟠 High |
| **BUG-006** | Android | Conversation stays on "Loading conversation…" and no AI response is generated | 🟠 High |
| **BUG-007** | Android | Pay in BDT fails with a raw SSL / admin configuration error message | 🟠 High |

### Themes across all testing

- **Payment flow is the weakest area.** Three bugs (BUG-003, BUG-004, BUG-007) and one failed test (TC-23) are payment-related: a modal overlapping the subscription card, a 404 on Stripe cancel, a raw gateway error for BDT, and no feedback when the network is off during payment.
- **Raw backend messages reach the user.** BUG-004 shows an internal API route and BUG-007 shows an admin configuration message. Both should be replaced with friendly errors.
- **Network errors are not handled gracefully.** No message appears when the connection drops during payment (TC-23, ET-13, ET-17).
- **Authentication screens are inconsistent.** A validation error for a field that does not exist (BUG-001), different layouts and wording between Welcome and Sign-in, and a pre-checked marketing consent box (ET-18, ET-20, UX-02, UX-03).
- **Chat reliability on Android needs attention.** A prompt is sent twice (BUG-005) and a long prompt can hang on loading (BUG-006).
- **Core features are stable.** Login with Google, prompting, model switching, Compare, Write, Translate, Read (PDF), history, dark mode, voice input and all five API checks behaved as expected.

---

## Tools and Techniques

| Type | Details |
|---|---|
| **Techniques** | Functional testing, exploratory testing, API testing, heuristic UI/UX review |
| **Tools** | Postman, browser DevTools (Network tab), Google Sheets |
| **Platforms** | Chrome extension (Chrome, Brave), Android app, REST API |

---

## Repository Structure

```text
.
├── README.md                        # This page
├── 01-functional-testing/
│   └── README.md
├── 02-exploratory-testing/
│   └── README.md
├── 03-api-testing-postman/
│   └── README.md
├── 04-ui-ux-review/
│   └── README.md
└── 05-bug-report/
    └── README.md
```

---

## Author

**Md. Shafiur Rahman**
