# Exploratory Testing — EchoGPT

[← Back to main report](../README.md)

[![Google Sheet](https://img.shields.io/badge/Sessions-Google%20Sheet-34A853?logo=googlesheets&logoColor=white)](https://docs.google.com/spreadsheets/d/1zX9DCun1FpW0InNQmD-_IkQO32p0yvJJO9Di-ekcbFE/edit?usp=sharing)

## Overview

| Field | Details |
|---|---|
| **Application** | EchoGPT (Chrome extension and Android app) |
| **Sessions** | 26 (ET-01 to ET-26) |
| **Focus** | Edge cases, usability observations and improvement recommendations beyond the scripted test cases |
| **Tested by** | Md. Shafiur Rahman |

Each session records the **area** explored, the **observation**, the **edge cases** tried, a **recommendation** and a **severity**.

## Summary

| Severity | Sessions |
|---|:---:|
| 🟠 High | 1 |
| 🟡 Medium | 5 |
| 🟢 Low | 20 |
| **Total** | **26** |

## Key Issues (Medium and High)

| ID | Area | Observation | Severity |
|---|---|---|---|
| **ET-13** | Payment Gateway Validation | Invalid card validation works with Wi-Fi on, but no feedback appears with Wi-Fi off, even after repeated retries | 🟠 High |
| **ET-03** | Create New Account | "First name is required" is shown although no First Name field is visible; reproducible after a refresh | 🟡 Medium |
| **ET-17** | Network Behavior | Server responses were correct, but the user sees no friendly network error or retry option | 🟡 Medium |
| **ET-20** | Authentication Flow | Welcome and Sign-in screens use different layouts and terminology | 🟡 Medium |
| **ET-22** | Profile Settings | Settings only shows profile information and Sign Out | 🟡 Medium |
| **ET-24** | MCP Connector | First-time users get little guidance for configuring an MCP server | 🟡 Medium |

## Edge Cases Explored

- **Email input:** unregistered email in valid syntax, uppercase letters and leading/trailing spaces.
- **Prompts:** short, long, multiline, special characters and emojis.
- **Usage limit:** repeated Send presses and refreshes after the limit was reached (no duplicate requests were processed).
- **Session handling:** reopening the extension after login and after sign out.
- **Chat management:** creating several new chats in a row and switching back to older ones (no data lost).
- **Copy:** short text, long responses, code blocks and multiline content.
- **Translation:** English to Bangla, Bangla to English, emojis, numbers and multiline text.
- **Voice input:** English, Bangla, numbers and punctuation.
- **Network:** Wi-Fi disabled during payment, temporary network interruption, invalid login.
- **Theme:** repeated Light/Dark switching and app restart.

## All Sessions

| ID | Area | Observation | Recommendation | Severity |
|---|---|---|---|---|
| ET-01 | Google Login | Sign-in succeeded and the session stayed active after reopening the extension | Keep persistent sessions; show a loading indicator during sign-in | 🟢 Low |
| ET-02 | Unregistered Email | Unregistered email is rejected with a clear message, including uppercase and padded input | Trim spaces automatically; add a direct Sign Up button | 🟢 Low |
| ET-03 | Create New Account | Validation error for a First Name field that is not on the form | Sync validation with visible fields | 🟡 Medium |
| ET-04 | AI Prompt & Model Response | Short, long, multiline, special-character and emoji prompts all returned relevant answers | Add a progress indicator and a Regenerate option | 🟢 Low |
| ET-05 | AI Model Switching | Model switching works and the selected model stays active | Show the active model more prominently; remember it across sessions | 🟢 Low |
| ET-06 | Free Usage Limit | Limit is enforced with a consistent message and reset time; no duplicate requests | Add a countdown timer with an upgrade option | 🟢 Low |
| ET-07 | Copy AI Response | Complete content copied, including code blocks and multiline text | Show a "Copied" toast message | 🟢 Low |
| ET-08 | Create New Chat | New chats open instantly; existing history is unchanged | Prompt users to rename or save important chats | 🟢 Low |
| ET-09 | Sign Out | Sign out works and the user stays signed out after reopening | Add a confirmation dialog before signing out | 🟢 Low |
| ET-10 | New Chat with Existing Conversation | No chat data lost or overwritten | Confirm only when the current chat has unsaved messages | 🟢 Low |
| ET-11 | Write Mode | Email, paragraph and rewrite prompts worked without UI issues | Add writing templates (Email, Cover Letter, Blog, Grammar Fix) | 🟢 Low |
| ET-12 | Translate Mode | Accurate translations in both directions for text, emojis, numbers and multiline input | Add automatic language detection and a Swap Languages button | 🟢 Low |
| ET-13 | Payment Gateway Validation | No feedback when Wi-Fi is off | Show a clear "No Internet Connection" message before processing | 🟠 High |
| ET-14 | Support Options | Email, WhatsApp and Facebook links open correctly | Add an in-app confirmation before opening external apps | 🟢 Low |
| ET-15 | Dark Mode | Applied across the app and persists after restart | Offer an option to follow the system theme | 🟢 Low |
| ET-16 | Voice Input | Accurate speech-to-text in a quiet environment | Add language selection and background noise handling | 🟢 Low |
| ET-17 | Network Behavior | Correct responses, but no user-friendly network error | Show a clear Network Error message with retry | 🟡 Medium |
| ET-18 | Sign In Popup | Marketing consent checkbox is pre-selected | Keep it unchecked by default | 🟢 Low |
| ET-19 | Welcome/Login | Primary login action is not prominent because of empty space | Use a centered layout with a stronger primary CTA | 🟢 Low |
| ET-20 | Authentication Flow | Inconsistent layouts and terminology across login screens | Use one consistent authentication design | 🟡 Medium |
| ET-21 | Home Dashboard | Large unused area after login | Show recent chats or suggested prompts | 🟢 Low |
| ET-22 | Profile Settings | Settings limited to profile and Sign Out | Add Edit Profile, Password, Theme and Notification settings | 🟡 Medium |
| ET-23 | History Chats | Few items, unused space and limited organisation | Add sorting, search and pinned conversations | 🟢 Low |
| ET-24 | MCP Connector | Limited onboarding for MCP server setup | Add setup examples, documentation and inline validation | 🟡 Medium |
| ET-25 | Message Composer Tools | Unlabeled action icons reduce discoverability | Add tooltips or group secondary tools in a "More" menu | 🟢 Low |
| ET-26 | Right Navigation Sidebar | Inconsistent spacing and a large gap before Upgrade and Settings | Use equal spacing and visual dividers | 🟢 Low |

## Related Documents

- Failed scripted tests that match these sessions: TC-03 (ET-03) and TC-23 (ET-13). See [Functional Testing](../01-functional-testing/).
- Interface observations from ET-18 to ET-26 were expanded in the [UI/UX Review](../04-ui-ux-review/).
- Confirmed defects are listed in the [Bug Report](../05-bug-report/).
