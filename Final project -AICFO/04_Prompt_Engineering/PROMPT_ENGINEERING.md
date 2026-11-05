🧠 Prompt Engineering — AI CFO

«Project: AI CFO — Intelligent Financial Management System
Author: Baraa Mahmoud Abu Watfa
Training: AI & Automation
Organization: Women's Affairs Center (WAC) — Freelancing Incubator
Technology Stack: Lovable · Supabase · n8n Cloud»

---

📌 1. Overview

Prompt Engineering played an important role in designing and developing AI CFO.

The prompts were structured to guide AI-powered development tools and services in building the application's interfaces, connecting backend services, implementing financial features, and supporting intelligent financial analysis.

The main objective was to provide clear instructions, define expected behavior, establish technical constraints, and reduce incorrect or incomplete outputs.

The prompts focused on:

- 🏗️ Application structure and user interfaces.
- 🔐 Authentication and company management.
- 💰 Financial transaction management.
- 📊 Dashboard calculations and financial indicators.
- 🧠 Financial intelligence and AI-generated insights.
- 📄 Financial reports and PDF generation.
- ⚙️ Workflow automation using n8n.
- 🛡️ Security, validation, and error handling.

🎯 2. Prompt Engineering Approach

The prompts followed a structured approach to improve the quality and reliability of AI-generated results.

Each prompt was designed to define:

Element| Description
Role| What the AI tool is expected to do
Context| Project background and technical environment
Objective| The specific feature or task
Requirements| Functional and technical requirements
Constraints| Rules and limitations that must be respected
Expected Output| The expected implementation or result
Validation| How the result should be checked

Prompt Design Principles

- Be specific about the requested task.
- Provide sufficient project context.
- Define the expected behavior clearly.
- Avoid implementing multiple unrelated features in one prompt.
- Preserve existing project structure and working functionality.
- Use real financial data instead of fabricated metrics.
- Include validation and error-handling requirements.
- Review the generated result before moving to the next stage.

---

🧩 3. Core Prompts

The following prompts document the main instructions used and adapted for the AI CFO development process.

3.1 Prompt 01 — Application Structure

Tool: Lovable
Purpose: Establish the main application structure and user interface.

Expected Result: A responsive application structure with the main pages and navigation.

Build a professional and maintainable web application named AI CFO.

The application is an intelligent financial management platform
designed to help small businesses understand and manage their
financial performance.

Create the following main pages:

- Landing Page
- Sign Up
- Login
- Company Setup
- Dashboard
- Transactions
- Financial Intelligence
- Financial Reports

Design Requirements:

- Use reusable and responsive UI components.
- Support Arabic (RTL) and English (LTR).
- Use a professional financial design system.
- Apply Navy, Steel Blue, Beige, and White as the main colors.
- Use light backgrounds for authenticated pages.
- Provide clear navigation between pages.
- Include loading, empty, success, and error states.
- Ensure compatibility with desktop, tablet, and mobile screens.

Important Constraints:

- Do not create fake financial data.
- Do not display fabricated financial metrics.
- Do not implement AI or automation in this stage.
- Preserve existing working functionality.

Start by reviewing the current project structure.
Implement only the requested application structure.

At the end, summarize:
1. Pages created or updated.
2. Components implemented.
3. Files changed.
4. Remaining configuration requirements.

3.2 Prompt 02 — Authentication and Company Management

Tool: Lovable + Supabase
Purpose: Implement user authentication and company-based access.

Expected Result: Users can register, log in, manage their company setup, and access authorized company data.

Connect the AI CFO application to the existing Supabase project.

Implement the following authentication features:

- User registration.
- User login.
- User logout.
- Session persistence.
- Protected application routes.
- Company onboarding.

Company Setup Requirements:

If an authenticated user does not belong to a company,
display a company setup form.

The form should collect:
- Company name.
- Primary currency.
- Required company information.

Company Roles:

- owner
- admin
- finance_manager
- viewer

Security Requirements:

- Use the existing database schema.
- Do not invent or rename existing tables.
- Respect the existing company membership structure.
- Enforce permissions using Supabase Row Level Security.
- Verify company membership before accessing company data.
- Never expose service-role keys or secret credentials
  in frontend code.
- Route protection must not replace database-level security.

If required tables, relationships, or policies are missing,
report the exact requirements before changing the schema.

Test:
- Registration.
- Login.
- Logout.
- Session persistence.
- Company setup.
- Unauthorized access.

3.3 Prompt 03 — Financial Transactions

Tool: Lovable + Supabase
Purpose: Build the financial transaction management feature.

Expected Result: Authorized users can manage income and expense records.

Implement the Financial Transactions module in AI CFO
using the existing Supabase database structure.

The module must support:

1. Adding income transactions.
2. Adding expense transactions.
3. Editing existing transactions.
4. Deleting transactions when authorized.
5. Searching transactions.
6. Filtering transactions by date and category.
7. Filtering by transaction type.

Transaction Information:

- Amount.
- Transaction type (income or expense).
- Category.
- Transaction date.
- Description.

Validation Requirements:

- Amount must be a valid positive number.
- Transaction type must be valid.
- Required fields must be completed.
- Date values must be valid.
- Currency must be consistent with company settings.

Permissions:

- Owners and authorized administrators can manage records.
- Finance managers can manage financial transactions.
- Viewers have read-only access.

Security Requirements:

- Respect Supabase RLS policies.
- Do not trust company identifiers supplied by the browser.
- Verify membership through trusted authorization rules.
- Do not expose sensitive credentials.

Ensure that transaction changes are reflected
in the related financial metrics.

Include loading, empty, success, and error states.

Do not generate mock transactions.

At the end, provide a summary of the implemented
functionality and a manual testing checklist.

3.4 Prompt 04 — Financial Dashboard

Tool: Lovable
Purpose: Display financial performance indicators using real company data.

Expected Result: A dashboard that accurately reflects the selected company's financial activity.

Build the AI CFO Dashboard using real financial transactions
from the currently selected company.

Display the following financial indicators:

- Total Revenue.
- Total Expenses.
- Net Financial Result.
- Cash Flow.

Dashboard Requirements:

- Use real transaction records.
- Apply the selected date range.
- Display revenue and expense trends.
- Provide clear financial summary cards.
- Use suitable charts and visualizations.
- Display expense categories.
- Keep the dashboard responsive.

Calculation Rules:

- Calculate financial values using application logic.
- Do not ask the AI model to calculate authoritative totals.
- Do not use fabricated or hardcoded financial metrics.
- Do not combine transactions from different currencies.
- Handle empty datasets correctly.
- Handle missing comparison periods without inventing values.

Security:

- Display data belonging only to the selected company.
- Respect user permissions and Supabase RLS.

Every dashboard component must support:
- Loading state.
- Empty state.
- Error state.

Verify that the displayed values match the underlying
financial transactions.

3.5 Prompt 05 — Financial Intelligence

Tool: Lovable + AI Integration
Purpose: Analyze financial data and generate evidence-based insights.

Expected Result: An intelligent financial analysis experience that helps users understand performance and identify unusual patterns.

Implement the Financial Intelligence feature in AI CFO.

The feature must analyze real financial data belonging
to the currently selected company.

Main Analysis Requirements:

1. Revenue trends.
2. Expense trends.
3. Net financial result.
4. Period-over-period comparisons.
5. Expense category analysis.
6. Unusual expense detection.
7. Financial alerts.
8. Evidence-based recommendations.

Data Processing Rules:

- Retrieve transactions for the selected company.
- Apply the selected date range.
- Validate data availability and currency consistency.
- Calculate financial metrics using deterministic application logic.
- Use AI only to interpret calculated results and generate insights.

AI Responsibilities:

- Explain important financial changes.
- Identify patterns that deserve attention.
- Interpret unusual expense signals.
- Generate clear and practical recommendations.

AI Restrictions:

- Never invent financial figures.
- Never fabricate transactions or evidence.
- Never present assumptions as confirmed facts.
- Do not claim a cause without supporting evidence.
- Clearly identify missing or insufficient data.
- Separate measured facts, hypotheses, and recommendations.

Display the results in a clear and organized interface.

Every important insight should be connected to the
financial evidence supporting it.

Respect company permissions and data privacy.

3.6 Prompt 06 — Financial Reports and PDF Export

Tool: Lovable
Purpose: Generate monthly and annual financial reports.

Expected Result: Accurate financial reports that can be viewed and exported as PDF files.

Implement the Financial Reports module in AI CFO.

The module must support:

- Monthly financial reports.
- Annual financial reports.
- Financial summary indicators.
- Revenue and expense analysis.
- Net financial result.
- Profit margin when the required data is available.
- Relevant charts and comparison tables.

Report Requirements:

- Use actual financial transactions.
- Respect the selected company.
- Apply the requested reporting period.
- Use consistent currency formatting.
- Ensure that report calculations match the Dashboard
  and Financial Intelligence data.

PDF Export:

Generate a professional PDF report.

The PDF must include:
- Company information.
- Report title.
- Reporting period.
- Financial summary.
- Relevant charts and tables.
- Currency information.
- Clear formatting and page layout.

Design Guidelines:

- Use Navy, Steel Blue, Beige, and White.
- Maintain a clean and professional appearance.
- Support readable Arabic and English content.
- Ensure that tables and charts fit within page boundaries.

Do not generate fake data or unsupported financial conclusions.

Verify that exported PDF values match the application data.

3.7 Prompt 07 — Monthly Financial Report Automation

Tool: n8n Cloud
Purpose: Automate the monthly financial report delivery.

Expected Result: The company owner receives the monthly financial report by email.

Create an n8n workflow named:

AI CFO - Monthly Financial Report

Objective:
Automatically prepare and email a monthly financial report
to the company owner.

Workflow Structure:

1. Schedule Trigger
   Run the workflow at the configured monthly schedule.

2. Get Company Information
   Retrieve the required company information.

3. Calculate Reporting Period
   Determine the reporting month.

4. Get Report Month Transactions
   Retrieve financial transactions for the reporting period.

5. Get Comparison Month Transactions
   Retrieve the previous period when comparison data exists.

6. Calculate Financial Metrics
   Calculate revenue, expenses, and net financial result
   using deterministic logic.

7. Generate HTML Monthly Report
   Prepare a structured and readable email report.

8. Gmail
   Send the report to the authorized company owner.

Requirements:

- Use the correct company data.
- Respect the reporting timezone.
- Validate the reporting period.
- Handle missing data.
- Avoid duplicate report delivery.
- Handle email failures.
- Store credentials securely in n8n.
- Never expose secrets in workflow output.

Do not use fabricated financial data.

Provide a clear description of each node,
its configuration, required credentials,
and expected output.

3.8 Prompt 08 — Unusual Expense Alert Automation

Tool: n8n Cloud
Purpose: Notify the company owner when an unusual expense requires review.

Expected Result: An alert is sent to the company owner with the relevant transaction details.

Create an n8n workflow named:

AI CFO - Unusual Expense Alert

Objective:
Detect unusual expense events and notify the company owner.

Workflow Structure:

1. Trigger
   Receive a new expense event from the authorized system.

2. Get Expense Information
   Retrieve the transaction details.

3. Check Expense
   Compare the expense against the configured detection rules
   and relevant financial history.

4. Evaluate Result
   Determine whether the expense requires attention.

5. Notify Owner
   Send an alert through the configured notification channel,
   such as Telegram or email.

Alert Information:

- Company name.
- Expense amount.
- Transaction date.
- Expense category.
- Transaction description.
- Reason for the alert.
- Transaction reference when available.

Important Rules:

- Do not automatically classify an unusual expense as fraud.
- Explain the reason behind every alert.
- Do not create alerts without supporting evidence.
- Avoid duplicate notifications.
- Handle missing or incomplete transaction data.
- Protect company and customer information.
- Store credentials securely.

Document each node and explain its configuration.

Test both unusual and normal expense scenarios.

3.9 Prompt 09 — Final Quality and Security Review

Tool: Lovable
Purpose: Review the existing application and identify confirmed issues.

Expected Result: A structured review of functionality, security, data accuracy, and usability.

Perform a quality and security review of the existing AI CFO
application.

Do not rebuild the application.
Do not rewrite working features.
Do not introduce new features.

Review the following areas:

1. Authentication and session handling.
2. Company membership and data isolation.
3. Supabase RLS policies.
4. User roles and permissions.
5. Transaction validation.
6. Financial calculation accuracy.
7. Currency consistency.
8. Dashboard data accuracy.
9. Financial Intelligence evidence.
10. Financial Reports and PDF export.
11. Monthly report automation.
12. Unusual expense alert automation.
13. Loading, empty, and error states.
14. Arabic and English localization.
15. Responsive design.

For every issue, report:

- Issue description.
- Affected feature.
- Reproduction steps.
- Expected behavior.
- Actual behavior.
- Severity.
- Suggested minimal fix.

Classify each test as:

- PASS
- FAIL
- NOT TESTED

Only mark a test as PASS when it has been
actually verified.

Fix only confirmed issues and avoid unnecessary changes.

Summarize the review findings and remaining risks.

---

🧪 4. Prompt Improvement Example

This example demonstrates how a general instruction can be improved by adding context, constraints, and measurable expectations.

4.1 Initial Prompt

Objective: Build a financial dashboard.

Build a dashboard for AI CFO that shows company
revenue, expenses, and profit.

4.2 Identified Limitations

The initial prompt does not specify:

- The source of financial data.
- Which transactions should be included.
- How financial metrics should be calculated.
- How different currencies should be handled.
- What should happen when no data exists.
- How company data should be protected.
- How the results should be validated.

As a result, the generated dashboard may contain incomplete functionality or inaccurate financial information.

4.3 Improved Prompt

Build the AI CFO Dashboard using real financial transactions
from the currently selected company.

Display:
- Total Revenue.
- Total Expenses.
- Net Financial Result.
- Cash Flow.

Requirements:

1. Retrieve data only for the selected company.
2. Use approved financial records according to the
   application's actual review rules.
3. Calculate financial metrics using deterministic logic.
4. Never use mock or fabricated financial data.
5. Never combine different currencies.
6. Display a clear empty state when no transactions exist.
7. Support date filtering and period comparisons.
8. Respect Supabase RLS and company membership.
9. Include loading and error states.
10. Validate the displayed results against the source records.

Before implementing changes, inspect the existing schema
and current dashboard structure.

Preserve working functionality and report any missing
database requirements instead of inventing them.

4.4 Improvement Analysis

Area| Initial Prompt| Improved Prompt
Context| Limited| Clear project context
Data source| Not specified| Real company transactions
Calculations| Not specified| Deterministic calculations
Security| Missing| RLS and company isolation
Currency| Missing| Currency consistency
Error handling| Missing| Loading, empty, and error states
Validation| Missing| Compare with source records

4.5 Improvement Outcome

The improved prompt provides clearer instructions and reduces ambiguity.

It also introduces validation rules that help prevent fabricated metrics, incorrect calculations, and unauthorized data access.

---

🛡️ 5. General Prompt Safety Rules

The following rules should be considered when writing or improving prompts for AI CFO:

- 🔒 Never expose API keys, passwords, or service-role credentials.
- 📊 Never allow AI to invent financial figures.
- 🧮 Keep authoritative financial calculations in application logic.
- 🔍 Require evidence for important financial observations.
- 👥 Respect company-level data isolation.
- ⚖️ Distinguish facts from assumptions and recommendations.
- 🧪 Include validation and failure scenarios.
- 🧩 Preserve existing working functionality.
- 📝 Request a summary of changes after implementation.
- 🚫 Do not claim successful execution without verification.

---

📈 6. Prompt Evaluation Criteria

Prompts should be evaluated based on the quality and reliability of their outputs.

Evaluation Criterion| Description
Clarity| Are the instructions understandable?
Completeness| Are the requirements sufficiently defined?
Relevance| Does the output match the requested feature?
Accuracy| Does the result use correct data and logic?
Security| Does it respect access and privacy requirements?
Consistency| Does it follow the project's existing structure?
Testability| Can the output be verified through test cases?
Maintainability| Can the implementation be maintained and improved?

📂 7. Conclusion

Prompt Engineering helped translate the AI CFO project requirements into structured instructions for AI-powered development and automation tools.

By defining clear objectives, technical requirements, constraints, and validation rules, the prompts supported a more organized development process.

The most important principle followed throughout the project was:

«AI should support the development and interpretation of financial information, while accuracy, security, and business rules remain controlled by the application.»

This approach helps make AI CFO more reliable, maintainable, and suitable for real-world financial management scenarios.
