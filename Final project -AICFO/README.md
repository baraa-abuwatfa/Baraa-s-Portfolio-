# 💼 AI CFO

**Intelligent Financial Management & AI-Powered Decision Support Platform**  
*Turning Financial Data into Intelligent Decisions.*

AI CFO helps small businesses and company owners manage financial activities, monitor performance, and understand their financial data through dashboards, reports, and AI-assisted insights.

## Project Documents

- [Client Proposal](./01-%20Client%20Proposal/CLIENT_PROPOSAL.md)
- [Working Prototype](./02_Technical_Solution/WORKING_PROTOTYPE.md)
- [System Architecture](./02_Technical_Solution/SYSTEM_ARCHITECTURE.md)
- [Prompt Engineering](./04_Prompt_Engineering/PROMPT_ENGINEERING.md)
- [Test Cases](./05-%20Testing/TEST_CASES.md)
- [Testing Evidence](./05-%20Testing/TESTING_EVIDENCE.md)
- [Final Project Report](./06-%20Documentation/Final%20Project%20Report.md)
- [Monthly Report Telegram Automation](./08_Automation/MONTHLY_REPORT_TELEGRAM_AUTOMATION.md)
- [n8n Workflow Setup](./08_Automation/N8N_WORKFLOW_SETUP.md)

## Core Features

- Authentication, company workspaces, and role-based access.
- Financial dashboard, transaction management, and reporting.
- AI-assisted financial analysis and conversational support.
- Monthly report PDF archival in Supabase Storage and configured monthly Telegram delivery automation.

## Monthly Report Telegram Automation

The existing AI CFO application generates and archives a monthly report PDF when a user exports a report. An n8n Cloud workflow is configured to run on day 2 of each month at 09:00 in the `Asia/Gaza` timezone, retrieve the latest report metadata for the configured company from Supabase, download the PDF from the private `financial-reports` bucket using the `storage_path` value in `report_files`, validate the binary, prepare an Arabic Telegram notification, and send the PDF document using the Telegram Bot API.

The workflow is implemented and configured. PDF archival in Supabase has succeeded, and Supabase report-metadata retrieval was previously successful. **End-to-end Telegram delivery of an actual PDF remains pending verification**; no successful delivery is claimed until the PDF is received in the configured Telegram chat. Manual testing is available through the Manual Test Trigger.

The automation uses Telegram, not email or SMTP. n8n orchestrates delivery; it does not generate the report PDF.

## Technology Stack

| Technology | Purpose |
|---|---|
| Lovable | Application interface development |
| Supabase / PostgreSQL | Authentication, application data, report metadata, and private PDF storage |
| AI integration | Financial analysis and decision-support insights |
| n8n Cloud | Monthly report retrieval and Telegram delivery orchestration |
| Telegram Bot API | Delivery of the archived PDF to the configured Telegram Chat ID |

## Project Structure

```text
Final project -AICFO/
├── 01- Client Proposal/
│   └── CLIENT_PROPOSAL.md
├── 02_Technical_Solution/
│   ├── WORKING_PROTOTYPE.md
│   ├── SYSTEM_ARCHITECTURE.md
│   └── screenshots/
├── 03_Content/
├── 04_Prompt_Engineering/
├── 05- Testing/
├── 06- Documentation/
└── 08_Automation/
    ├── MONTHLY_REPORT_TELEGRAM_AUTOMATION.md
    ├── N8N_WORKFLOW_SETUP.md
    └── screenshots/
```

## Important Notes

- AI-generated financial insights are decision-support information and require human review.
- Report PDFs are generated and archived by the application when users export reports; n8n retrieves and sends the archived file.
- Telegram delivery should be described as configured, but successful end-to-end delivery remains unverified until a real PDF is received.
- Never commit bot tokens, Supabase secrets, private keys, passwords, or real customer financial data.

## Project Information

**Project:** AI CFO – Intelligent Financial Management Platform  
**Prepared by:** Baraa Mahmoud Abu Watfa  
**Program:** AI-Powered Solution Engineering  
**Organization:** Women's Affairs Center – Gaza
