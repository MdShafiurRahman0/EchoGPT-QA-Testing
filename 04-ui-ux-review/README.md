# UI/UX Review — EchoGPT

[← Back to main report](../README.md)

[![Google Sheet](https://img.shields.io/badge/UI%2FUX%20Review-Google%20Sheet-34A853?logo=googlesheets&logoColor=white)](https://docs.google.com/spreadsheets/d/1aYE7dZlFGglq2MiC3P0CGkayBfPWmMcB8noeB-u-njM/edit?usp=sharing)

## Overview

| Field | Details |
|---|---|
| **Application** | EchoGPT Chrome extension |
| **Observations** | 10 (UX-01 to UX-10) |
| **Focus** | Layout, visual hierarchy, consistency, discoverability and onboarding |
| **Tested by** | Md. Shafiur Rahman |

Each observation describes the **screen**, what is **wrong or missing**, and a concrete **recommendation**. Several of them expand earlier exploratory sessions, which are linked in the last column.

## Summary

| ID | Screen | Observation | Related exploratory session |
|---|---|---|---|
| UX-01 | Welcome/Login | Too much empty space; primary login actions are not visually prioritised | ET-19 |
| UX-02 | Sign In popup | "I want to receive updates" checkbox is enabled by default | ET-18 |
| UX-03 | Welcome and Sign-in | The two screens differ in CTA style, options, wording, layout and navigation | ET-20 |
| UX-04 | Chat Dashboard (Home) | Large unused area below the suggested prompts | ET-21 |
| UX-05 | Profile icon / Settings | Settings only shows the profile and a Sign Out button | ET-22 |
| UX-06 | History Chats | Unused space, limited history management, truncated titles | ET-23 |
| UX-07 | MCP Connector | Little guidance for first-time MCP server setup | ET-24 |
| UX-08 | Message Composer | Many small unlabeled icons reduce discoverability | ET-25 |
| UX-09 | Right Navigation Sidebar | Inconsistent spacing and a large empty gap before Upgrade and Settings | ET-26 |
| UX-10 | Message Composer (input area) | Send button looks disabled, Search is unclear, helper text is too small | — |

## Detailed Findings

<details>
<summary><b>UX-01</b> — Welcome/Login: weak visual hierarchy</summary>

**Observation:** The welcome screen has excessive empty space and the primary login actions are not visually prioritised.

**Recommendations**
- Use a cleaner, centered layout.
- Make **Continue with Email** a filled primary button and keep Google sign-in as a secondary option.
- Replace "Create New Account" with "Already have an account? Log in" for a clearer CTA hierarchy.

**Related:** ET-19
</details>

<details>
<summary><b>UX-02</b> — Sign In popup: marketing consent pre-selected</summary>

**Observation:** The "I want to receive updates" checkbox is enabled by default, which can confuse users about marketing consent.

**Recommendations**
- Keep the checkbox unchecked by default.
- Let users opt in voluntarily.

**Related:** ET-18
</details>

<details>
<summary><b>UX-03</b> — Welcome and Sign-in: inconsistent authentication design</summary>

**Observations**
- The Welcome screen uses an outlined Email button, while the popup uses a filled Google button as the primary CTA.
- The Welcome screen offers 3 authentication options, while the popup offers 4 social login options.
- Terminology differs: "Create New Account" vs. "Sign up for free".
- Background, spacing and layout differ significantly between the two screens.
- Navigation is inconsistent: the popup has a back button, the Welcome screen does not.

**Recommendations**
- Create one unified authentication design for all login screens.
- Use the same primary call-to-action, identical login options and the same terminology.
- Keep spacing, typography and background styling consistent.
- Apply the same navigation pattern on both screens.

**Related:** ET-20
</details>

<details>
<summary><b>UX-04</b> — Chat Dashboard (Home): unused space</summary>

**Observation:** A large unused area below the suggested prompts makes the interface feel incomplete and lowers information density.

**Recommendations**
- Show recent chats, pinned conversations, onboarding tips or more suggested prompts in that space.

**Related:** ET-21
</details>

<details>
<summary><b>UX-05</b> — Profile icon / Settings: incomplete settings</summary>

**Observation:** The Settings modal only displays the user profile and a Sign Out button. Users cannot manage profile editing, password, notifications or appearance.

**Recommendations**
- Add Edit Profile and Change Password.
- Add Notification Preferences.
- Add a Dark/Light Theme option and Language Settings.

**Related:** ET-22
</details>

<details>
<summary><b>UX-06</b> — History Chats: limited organisation</summary>

**Observations**
- Only a few chats are shown, with a large empty area below the list.
- History management features are very limited.
- Long chat titles are truncated without a way to read the full title.

**Recommendations**
- Show recent, pinned or favorite chats in the empty space.
- Add sort options (Newest, Oldest, A to Z).
- Support multi-select delete instead of single delete only.
- Show the total number of chats at the top.
- Show the full title on hover or through a tooltip.

**Related:** ET-23
</details>

<details>
<summary><b>UX-07</b> — MCP Connector: weak first-time guidance</summary>

**Observation:** The empty state gives limited guidance to first-time users configuring an MCP server.

**Recommendations**
- Add onboarding instructions and an example configuration.
- Link to setup documentation or a quick tutorial.
- Add inline validation and clearer errors for invalid URLs.

**Related:** ET-24
</details>

<details>
<summary><b>UX-08</b> — Message Composer: unlabeled icons</summary>

**Observation:** The composer has several small action icons (Scissors, Attachment, Read, @, Sparkles, User) with no labels. New users may not understand what each one does.

**Recommendations**
- Group related tools into a "More" menu or show tooltips on hover.
- Keep only the most-used actions visible.
- Add text labels or onboarding hints.

**Related:** ET-25
</details>

<details>
<summary><b>UX-09</b> — Right Navigation Sidebar: spacing and clarity</summary>

**Observation:** Spacing between menu items is inconsistent and there is a large empty area before the Upgrade and Settings section. Small icons and labels reduce clarity for first-time users.

**Recommendations**
- Keep equal vertical spacing between all navigation items.
- Remove the large gap by grouping bottom actions with the main navigation.
- Slightly increase icon and label size.
- Separate Settings and Upgrade with a visual divider instead of whitespace.

**Related:** ET-26
</details>

<details>
<summary><b>UX-10</b> — Message Composer (input area): low visual clarity</summary>

**Observation:** The Send button looks disabled without any guidance, the Search action is unclear, and the helper text ("Enter to send · Shift+Enter new line") is too small to notice.

**Recommendations**
- Increase the visibility of the helper text.
- Add a tooltip or label that explains Search.
- Clearly show when the Send button becomes active after typing.
- Improve placeholder contrast so the input field stands out.
</details>

## Related Documents

- Exploratory sessions behind these observations: [Exploratory Testing](../02-exploratory-testing/)
- Confirmed defects: [Bug Report](../05-bug-report/)
