# Project: SharePoint List Data Harmonizer Bot

## 1. Problem Statement
**Inefficient and Inaccurate User Data Synchronization for SharePoint Lists**

The current manual process of maintaining user information across disparate sources (Box, Smartsheet, and SharePoint) creates significant operational friction and data integrity issues, specifically:

* **Data Staleness:** User attributes become inconsistent across platforms, breaking automated workflows and reporting.
* **Manual Overhead:** Administrators spend excessive time manually querying different APIs to reconcile SharePoint lists.
* **Delayed Information:** Manual updates cause a lag, meaning SharePoint lists often do not reflect real-time user status.

---

## 2. Proposed Solution
A specialized **AI-driven Chatbot** that serves as a centralized point for querying and verifying user information across Box, Smartsheet, and SharePoint.

### Key Capabilities:
* **On-Demand Retrieval:** Fetch specific user details (e.g., "What is N's department in Smartsheet?") instantly.
* **Proactive Verification:** Automatically compare user attributes across platforms and report discrepancies.
* **Targeted List Updates:** Use AWS Lambda to fetch the latest API data and automate the update process for SharePoint entries.

---

## 3. Technical Architecture
The solution leverages a serverless architecture to ensure scalability and ease of integration.

### Core Components:
1.  **Amazon Lex (Conversational Interface):** Handles Natural Language Understanding (NLU) to identify user intent and collect required data via "Slots."
2.  **AWS Lambda (Backend Logic):** Acts as the "brain," performing the API calls to Box, Smartsheet, and SharePoint.
3.  **External APIs:** Securely connects to the various platforms to fetch or push data.



---

## 4. Bot Design: Intents & Slots
To handle multiple use cases within a single bot, we use a modular design:

| Intent | Description | Key Slots (Parameters) |
| :--- | :--- | :--- |
| **VerifyUserAccess** | Compares Box/Smartsheet permissions with SharePoint. | `UserName`, `TargetApplication` |
| **QueryFilePermissions** | Checks what files or folders a specific user can access. | `UserName`, `FileType` |
| **QuerySheetHoldings** | Lists the Smartsheet sheets owned or accessed by a user. | `UserName` |
| **UpdateSharePointList** | Automates the data sync from external sources to SharePoint. | `UserName`, `ListID` |

---

## 5. Impact & Goals
* **Automation:** Frees up administrative time for high-value tasks.
* **Data Governance:** Shifts from reactive "firefighting" to proactive data management.
* **Reliability:** Ensures SharePoint lists remain a "Single Source of Truth" for Power Automate triggers.

---
**Next Steps:** * Complete the AWS Lambda integration for the `VerifyUserAccess` intent.
* Configure IAM roles for secure API authentication with Box and Smartsheet.
