# Functional Testing — EchoGPT

[← Back to main report](../README.md)

[![Google Sheet](https://img.shields.io/badge/Test%20Cases-Google%20Sheet-34A853?logo=googlesheets&logoColor=white)](https://docs.google.com/spreadsheets/d/1FwJLr35Q-L4Uh9ePLh0ot-wjGpkEkUm4WYPQymxh424/edit?usp=sharing)

## Overview

| Field | Details |
|---|---|
| **Application** | EchoGPT (Chrome extension and Android app) |
| **Test cases** | 30 (TC-01 to TC-30) |
| **Platforms** | Chrome Extension (TC-01 to TC-20), Android App (TC-21 to TC-30) |
| **Account type** | Free plan |
| **Tested by** | Md. Shafiur Rahman |

## Scope

**Chrome Extension (20 test cases):** Google login, login with an unregistered email, account creation, sending prompts, switching AI models, free usage limit, copying responses, new chat, sign out, chat history, session persistence, reopening previous conversations, Write, Translate, Read (PDF), Image, Video, Compare and MCP connector modes.

**Android App (10 test cases):** Google login, sending a prompt, international payment validation, comparing responses across multiple models, support options, dark mode, sharing the app, logout, notifications and voice input.

## Results

| Platform | Total | Pass | Fail | Not recorded |
|---|:---:|:---:|:---:|:---:|
| Chrome Extension | 20 | 19 | 1 | 0 |
| Android App | 10 | 8 | 1 | 1 |
| **Total** | **30** | **27** | **2** | **1** |

Failed tests: **TC-03** (Create New Account) and **TC-23** (International Payment Gateway Validation). Details are below.

## Chrome Extension Test Cases

| ID | Feature | Result | Notes |
|---|---|:---:|---|
| TC-01 | Login with Google | ✅ Pass | Home sidebar opened after sign-in |
| TC-02 | Login with Unregistered Email | ✅ Pass | Login rejected with a clear message; no verification code sent |
| TC-03 | Create New Account | ❌ Fail | Wrong validation message (see below) |
| TC-04 | Send a valid prompt using the default model | ✅ Pass | |
| TC-05 | Change AI model and send prompt | ✅ Pass | |
| TC-06 | Usage limit reached | ✅ Pass | Free plan limit of 5 messages per 5-hour window; reset time shown |
| TC-07 | Copy AI response | ✅ Pass | Full response copied and pasted correctly |
| TC-08 | Create new chat | ✅ Pass | |
| TC-09 | Sign out | ✅ Pass | Redirected to the Welcome screen |
| TC-10 | Open history | ✅ Pass | |
| TC-11 | Create new chat while an existing chat is open | ✅ Pass | Previous chats stayed in History |
| TC-12 | Reopen extension after login | ✅ Pass | Session stayed active |
| TC-13 | Reopen previous conversation | ✅ Pass | |
| TC-14 | Open Write mode | ✅ Pass | |
| TC-15 | Open Translate mode | ✅ Pass | |
| TC-16 | Open Read mode | ✅ Pass | PDF uploaded and summarised |
| TC-17 | Open Image mode | ✅ Pass | Paid-only message shown for the Free plan |
| TC-18 | Open Video mode | ✅ Pass | Paid-only message shown for the Free plan |
| TC-19 | Open Compare mode | ✅ Pass | Responses from several models shown |
| TC-20 | Open MCP Connector page | ✅ Pass | Add Connector form with Name, Server URL and Authorization Header |

## Android App Test Cases

| ID | Feature | Result | Notes |
|---|---|:---:|---|
| TC-21 | Login with Google | ✅ Pass | |
| TC-22 | Send a valid prompt | ⚪ Not recorded | Steps documented; expected result, actual result and status not filled in |
| TC-23 | International payment gateway validation | ❌ Fail | No feedback when Wi-Fi is off (see below) |
| TC-24 | Compare responses across multiple AI models | ✅ Pass | All 5 models responded; one answer was less relevant than the others |
| TC-25 | Verify support options (Email, WhatsApp, Facebook) | ✅ Pass | |
| TC-26 | Switch to Dark Mode | ✅ Pass | |
| TC-27 | Share app | ✅ Pass | Play Store link shared through the share sheet |
| TC-28 | Log out | ✅ Pass | |
| TC-29 | Open notifications | ✅ Pass | |
| TC-30 | Voice input (speech-to-text) | ✅ Pass | |

## Failed Test Cases

### TC-03 — Create New Account (Chrome Extension)

| Field | Details |
|---|---|
| **Preconditions** | Extension installed; user is on the Create Account page |
| **Steps** | 1. Open the extension<br>2. Click Create New Account<br>3. Enter only a valid email address<br>4. Click Send Verification Code |
| **Expected** | The system validates the visible Email field only, or shows the correct required-field message for the current form |
| **Actual** | The system shows "First name is required" although no First Name field exists |
| **Status** | ❌ Fail |
| **Related** | BUG-001, exploratory session ET-03 |

### TC-23 — International Payment Gateway Validation (Android)

| Field | Details |
|---|---|
| **Preconditions** | User is logged in, the Premium subscription page is open and an international payment method is selected |
| **Steps** | 1. Go to Upgrade and select a Premium plan<br>2. Choose Card / International payment<br>3. Wi-Fi ON: enter an invalid card number and observe the validation message<br>4. Wi-Fi OFF: disable Wi-Fi and try to continue the payment |
| **Expected** | Wi-Fi ON: the gateway validates the card and shows a validation message. Wi-Fi OFF: the app shows a network error or payment failure message |
| **Actual** | Wi-Fi ON: "Your card number is invalid." was shown (correct). Wi-Fi OFF: no network error or feedback was shown |
| **Status** | ❌ Fail |
| **Related** | Exploratory session ET-13 (severity High) |

## Test Case Template

| Column | Description |
|---|---|
| Test Case ID | Unique ID (`TC-01` and up) |
| Feature | Feature or screen under test |
| Preconditions | State required before the test |
| Test Steps | Steps to execute |
| Expected Result | Correct system behaviour |
| Actual Result | Observed behaviour |
| Status | Pass / Fail |
