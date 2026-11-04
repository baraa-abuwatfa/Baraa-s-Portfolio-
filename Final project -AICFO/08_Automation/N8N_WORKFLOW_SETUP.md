# ⚙️ n8n Workflow Setup — Monthly Report Telegram Delivery

## Purpose

This guide documents the setup and verification of the existing n8n Cloud workflow that retrieves an AI CFO monthly report PDF from private Supabase Storage and sends it using Telegram Bot API.

The AI CFO application generates and archives the PDF when a user exports a monthly report. n8n retrieves the archived file; it does not generate the PDF.

## Prerequisites

- Access to the authorized n8n Cloud workspace.
- Supabase project access and least-privilege credentials that can read the required `report_files` metadata and private `financial-reports` objects.
- Telegram bot configured and authorized for the destination chat.
- A configured company and Telegram Chat ID.
- A PDF already exported by the application and archived in Supabase.

Do not add real credentials, bot tokens, passwords, private keys, or secret values to this file or source control. Configure secrets through protected n8n credential facilities.

## Workflow Configuration

### Trigger

- Schedule: every month, day 2, at 09:00.
- Timezone: `Asia/Gaza`.
- Manual test: Manual Test Trigger.

### Supabase Metadata Lookup

- Query the `report_files` table for the latest monthly report associated with the configured company.
- Use the actual storage-path field `storage_path`.
- Define the appropriate period/company selection logic in the deployed workflow and verify it against the real schema; do not assume undocumented columns.
- Branch explicitly when no matching report is found.

### Private PDF Download

- Bucket: `financial-reports`.
- Visibility: Private.
- Object key/path: value from `storage_path`.
- Retrieve using authorized Supabase access; do not make the bucket public to simplify delivery.

### Validation and Telegram Delivery

- Confirm the downloaded binary is present and is a valid PDF before sending.
- Prepare a professional Arabic notification.
- Configure Telegram Bot API document delivery to the intended Telegram Chat ID.
- Confirm the correct binary property/file is mapped to the Telegram document input.

## Recommended Node Sequence

The exact visible node labels can vary by workflow version; preserve the behavior and verify mappings in the live n8n workflow.

1. Monthly Schedule Trigger and Manual Test Trigger.
2. Configuration / company and destination settings.
3. Supabase query for latest report in `report_files`.
4. Report-found conditional branch.
5. Supabase Storage download using `financial-reports` and `storage_path`.
6. PDF binary validation.
7. Arabic Telegram message preparation.
8. Telegram Bot API Send Document.
9. Failure handling / execution outcome.

## Security Checklist

- [ ] Supabase credential is stored in protected n8n credentials.
- [ ] Telegram bot token is stored in protected n8n credentials.
- [ ] No credential or token is embedded in node text, expressions committed to GitHub, screenshots, or logs.
- [ ] Storage bucket remains private.
- [ ] Access is restricted to the required company/report data.
- [ ] Destination Chat ID is configured securely and verified.
- [ ] Logs and screenshots contain no sensitive financial data or secret URLs.

## Manual Test Procedure

1. Use a non-sensitive test company/report and ensure the application has exported and archived the monthly PDF.
2. Verify the report record is available in `report_files` and inspect `storage_path` through authorized tools.
3. Start the workflow using Manual Test Trigger.
4. Confirm the report lookup selects the intended latest report for the configured company.
5. Confirm the PDF download and binary validation succeed.
6. Confirm the Telegram API request completes without exposing the bot token.
7. Open the configured Telegram chat and verify the actual PDF arrives and opens.
8. Record the observed outcome and add a redacted screenshot to `screenshots/` only if captured.

Do not mark end-to-end delivery passed until step 7 is verified. Supabase PDF archival has succeeded and metadata retrieval was previously successful, but Telegram PDF receipt remains pending verification until that test is completed.

## Failure Checks

- Missing report metadata must not lead to an attempted send.
- Supabase errors, missing storage objects, or invalid PDF data must stop the send path.
- Telegram API errors must be visible as failed executions, not success.
- Review retry behavior to avoid unintended duplicate documents.

## Troubleshooting Evidence

Store only actual, redacted workflow screenshots or test evidence in `./screenshots/`. Avoid screenshots containing access tokens, bot credentials, signed/private URLs, financial records, or personal chat details.
