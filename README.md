

# 🛡️ Remedy8 - Manual QA Testing Project: New Audit Workspace

![Status](https://img.shields.io/badge/Status-Completed-success)
![Testing](https://img.shields.io/badge/Testing-Manual-blue)
![Environment](https://img.shields.io/badge/OS-Windows%2011%20Pro-lightgrey)
![Browser](https://img.shields.io/badge/Browser-Chrome%20v152.0.7977.83-orange)

## 📌 Project Overview
This repository contains the comprehensive manual QA testing artifacts for **Remedy8**, an AI-powered audit and remediation management platform. 

Remedy8 is designed to consolidate the audit lifecycle from planning to evidence collection and closure into a controlled workspace. A key differentiator of the platform is its "Auditor-controlled AI," which helps generate audit objectives, methodologies, and risk focuses while ensuring the human auditor remains the final decision-maker.

### 🎯 Scope of Testing
The primary focus of this QA phase was the **"New Audit" creation workflow** accessed via the **My Dashboard**. I thoroughly tested the end-to-end audit creation process across three distinct phases:
1.  **Basics Phase:** Audit identity, naming, and period selection.
2.  **Plan Phase:** Workplan relationships, audit frequency, risk rating, and methodology methods.
3.  **Scope Phase:** AI-assisted drafting of objectives, methodology, risk focus, and resource planning.

## 🧪 Test Environment
*   **Operating System:** Windows 11 Pro
*   **Browser:** Google Chrome (Version 152.0.7977.83 - Official Build, 64-bit)
*   **Test Account Role:** Auditor (Logged in as *Nathan Daniel*)

## 🗂️ Test Artifacts & Methodology
The testing followed a structured manual testing approach. The project workbook is organized into the following sheets:
*   **Test Scenarios:** High-level validation goals (e.g., Dashboard, Search, New Audit).
*   **Test Cases:** A detailed register of **90+ test cases** covering functional, UI, negative, and validation testing. Each case includes pre-conditions, step-by-step actions, test data, and expected vs. actual results.
*   **Bug Report:** A curated list of 7 defects identified during the test cycle, linked directly to their failing test cases.

### 🧠 Highlight: AI Feature Testing
A significant portion of the Scope phase testing focused on the **"Draft"** and **"Refine"** AI buttons. I validated that:
*   AI successfully generated contextually relevant text for fields like Audit Objective, Methodology, and Risk Focus.
*   The UI correctly toggled button labels from "Draft" to "Refine" after initial generation.
*   Manual text entry appropriately did *not* trigger AI confirmation toasts.
*   Toast notifications properly auto-dismissed after ~5 seconds.

## 🐛 Key Findings & Bug Summary
Testing uncovered **7 distinct defects**. While severity and priority were marked as *Pending Assessment* (as per the project parameters), they can be logically grouped into the following areas:

| Bug ID | Area | Description | Impact |
| :--- | :--- | :--- | :--- |
| **BUG_AUD_001** | UI / Functionality | **Year and Quarter dropdowns unresponsive:** Clicking options in the dropdown fails to select them. | Blocks users from setting the Audit Period. |
| **BUG_AUD_002** | Validation | **Required fields bypassed (Basics):** Users can proceed to the Plan phase even when required Audit Name and Period fields are empty. | High - Data integrity risk. |
| **BUG_AUD_003** | UX | **No unsaved-changes warning:** Navigating back to "My Audits" from the Basics step silently discards entered data. | Potential loss of user work. |
| **BUG_AUD_005** | Validation | **Required fields bypassed (Scope):** Users can proceed to the Launch step without filling out mandatory fields (Objective, Scope, Methodology, Risk Focus). | High - Leads to incomplete audit setups. |
| **BUG_AUD_006** | UX | **No unsaved-changes warning (Scope):** Leaving the Scope step with typed data results in silent data loss. | Potential loss of user work. |
| **BUG_AUD_004 & 007** | UI / Layout | **Floating Widget Overlap:** The "Ask Remedy8" AI widget overlaps and obscures the "Continue" button on both the Plan and Scope steps. | Poor UX; button remains clickable but is visually obstructed. |

## 🚧 Limitations & Blocked Tests
*   **TC_AUD_020 (Blocked):** I attempted to verify the dependent relationship fields by changing the "Workplan" dropdown. However, the testing environment only offered one option ("Outside workplan"), making it impossible to test the alternate state. 

## 📝 Recommendations for the Dev Team
1.  **Implement Strict Validation:** Ensure front-end validation gates block progression when `[REQUIRED]` fields are empty across all phases.
2.  **Add Navigation Guards:** Implement a "You have unsaved changes. Leave anyway?" modal when users attempt to leave a form with dirty state.
3.  **Fix Dropdown Logic:** Investigate the state management issue preventing Year/Quarter selection.
4.  **Z-Index Adjustment:** Adjust the CSS `z-index` of the floating "Ask Remedy8" widget so it never overlaps critical navigation buttons.

### 📂 Project Files
*   [View the raw Test Cases](./test-cases/Remedy8_Test_Cases.csv)
*   [View the Bug Report](./bug-report/Remedy8_Bug_Report.csv) 
*   [Download the Master Excel Workbook](./Remedy8_QA_Project.xlsx)

