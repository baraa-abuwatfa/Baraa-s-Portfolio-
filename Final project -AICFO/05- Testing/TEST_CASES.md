# 🧪 AI CFO — Test Cases

## 1. Testing Overview

Functional testing documentation covers authentication and navigation, company management, the financial dashboard, transaction management, financial intelligence, financial reports, and the AI Financial Assistant. Existing recorded test results are summarized in [Testing Evidence](./TESTING_EVIDENCE.md).

The monthly Telegram report workflow is documented as implemented and configured. Its end-to-end document delivery must be tested separately; no success is claimed until an actual PDF is received in Telegram.

## 2. Existing Application Test Coverage

| Module | Recorded functional cases | Previously recorded status |
|---|---:|---|
| Authentication and Navigation | 6 | Passed |
| Company Management | 6 | Passed |
| Financial Dashboard | 8 | Passed |
| Transaction Management | 10 | Passed |
| Financial Intelligence | 10 | Passed |
| Financial Reports | 10 | Passed |
| AI Financial Assistant | 10 | Passed |
| **Total** | **60** | **Passed** |

Separately recorded automated tests: Authentication & Navigation — 30 executions; Invoice Tests — 58 executions; total 88. These are not added to the 60 functional scenarios.

## 3. Monthly Telegram Automation Test Cases

| ID | Scenario | Test outline | Expected result | Evidence/status |
|---|---|---|---|---|
| AUTO-001 | Schedule configuration | Inspect schedule configuration in n8n. | Monthly trigger is day 2 at 09:00 in `Asia/Gaza`. | Configured; retain redacted evidence if captured. |
| AUTO-002 | Manual trigger | Start workflow using Manual Test Trigger. | Workflow begins without waiting for the monthly schedule. | To be recorded. |
| AUTO-003 | Latest report lookup | Query `report_files` for the latest monthly report for the configured company. | Correct report metadata is found; workflow uses the `storage_path` column. | Supabase retrieval previously successful; retain execution evidence if available. |
| AUTO-004 | Missing report | Test with a company/period without report metadata. | No download or Telegram send occurs; the missing-report outcome is visible. | To be tested/recorded. |
| AUTO-005 | Private PDF download | Download the archived PDF from private `financial-reports` storage. | Authorized retrieval returns the intended PDF binary without making the bucket public. | PDF archival successful; record a specific download execution. |
| AUTO-006 | PDF validation | Test absent or invalid binary in a controlled environment. | Invalid/non-PDF data is stopped before Telegram send. | To be tested/recorded. |
| AUTO-007 | Arabic message preparation | Inspect the notification prepared for a valid report. | Professional Arabic notification accompanies the correct report. | To be recorded. |
| AUTO-008 | Telegram document delivery | Send an actual archived PDF to the configured Telegram Chat ID. | PDF arrives and opens in the destination chat. | **Pending end-to-end verification.** |
| AUTO-009 | Telegram API failure | Use a controlled invalid test configuration or safe failure scenario. | Workflow reports failure; it does not claim delivery succeeded. | To be tested/recorded. |
| AUTO-010 | Credential privacy | Inspect repository content and evidence before committing. | No bot token, private key, password, or secret is committed. | Verify before every commit. |

## 4. Workflow Under Test

The application generates and archives the PDF when the user exports a monthly report. The n8n Cloud workflow runs on the monthly schedule (day 2, 09:00, `Asia/Gaza`) or Manual Test Trigger, retrieves report metadata from Supabase `report_files`, downloads the PDF from the private `financial-reports` bucket via `storage_path`, validates the binary, prepares an Arabic Telegram notification, and sends the PDF using the Telegram Bot API.

## 5. Result Recording Rules

- Record only observed results and link actual, redacted evidence.
- A successful Supabase query or n8n execution does not prove that the document arrived.
- Mark Telegram delivery passed only after the actual PDF has been received and opened in the configured Telegram chat.
- Do not include credentials or real customer financial information in test evidence.
