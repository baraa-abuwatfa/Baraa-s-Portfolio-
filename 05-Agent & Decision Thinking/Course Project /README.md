# 🏡 XYZ Real Estate AI Agent

An AI-powered real estate lead qualification system built with **n8n, Telegram, OpenRouter, Simple Memory, and Google Sheets**.

## 📌 1. Project Overview

XYZ Real Estate AI Agent is an AI-powered assistant designed to collect and organize customer requirements for buying or renting properties.

The agent communicates with customers through Telegram, understands their messages, remembers information shared during the conversation, identifies missing details, and validates the collected information.

Before saving a lead, the agent presents a summary for customer review and requires explicit confirmation. Once confirmed, the system saves the information to Google Sheets and verifies the result before reporting success.

🎯 The goal is to build an AI agent that makes decisions, follows business rules, and executes actions under controlled conditions.

## 🚨 2. Business Problem

Real estate companies need accurate customer information to understand property requirements and follow up with potential buyers and renters.

Manual data collection can lead to:

- ❌ Missing or incomplete customer details.
- 🔁 Repeated questions and inefficient communication.
- ⚠️ Invalid or inconsistent information.
- 📄 Incorrect records and duplicate entries.
- 🔒 Data being saved without customer confirmation.

## 💡 3. Proposed Solution

The AI agent automates the lead collection process by:

- 💬 Receiving customer messages through Telegram.
- 🧠 Understanding natural-language responses.
- 📝 Collecting information in any order.
- 💾 Remembering previous answers during the conversation.
- 🔎 Asking only for missing or unclear information.
- ⚙️ Applying conditional business rules.
- ✅ Validating required fields and email addresses.
- 🤝 Requesting confirmation before saving information.
- 📊 Saving confirmed leads to Google Sheets.
- 🔍 Verifying the saving result before notifying the customer.

## 🎯 4. Project Objectives

- 🤖 Automate real estate lead collection.
- ⏱️ Reduce unnecessary questions and manual data entry.
- 🧠 Maintain conversation context across multiple messages.
- 📋 Improve data accuracy and consistency.
- 🔐 Prevent saving information before customer confirmation.
- 📊 Store customer records in the correct format.
- ⚠️ Handle saving failures accurately.

## 🛠️ 5. Technology Stack

| Technology | Purpose |
|---|---|
| 🔄 n8n | Workflow automation and agent orchestration |
| 💬 Telegram Bot | Customer communication |
| 🤖 AI Agent | Understands messages and determines the next action |
| 🧠 OpenRouter Chat Model | Language understanding and response generation |
| 💾 Simple Memory | Maintains conversation context |
| 📊 Google Sheets | Stores confirmed customer leads |

## 🔗 6. System Architecture

The workflow connects Telegram, the AI agent, and the response node. The agent also uses its connected model, memory, and Google Sheets tool.

```text
👤 Customer
     |
     v
💬 Telegram Trigger
     |
     v
🤖 AI Agent
     |
     +---- 🧠 OpenRouter Chat Model
     |
     +---- 💾 Simple Memory
     |
     +---- 📊 Google Sheets Tool
     |
     v
📨 Telegram Send Message
     |
     v
👤 Customer
```

⚠️ **Important:** The actual workflow must prevent Google Sheets from writing data before explicit customer confirmation.

### 🧩 Component Responsibilities

- 💬 **Telegram Trigger:** Receives incoming customer messages.
- 🤖 **AI Agent:** Interprets customer needs, tracks missing information, applies business rules, and determines the next step.
- 🧠 **OpenRouter Chat Model:** Processes natural language and generates responses.
- 💾 **Simple Memory:** Retains relevant conversation context between messages.
- 📊 **Google Sheets Tool:** Adds confirmed customer records to the spreadsheet.
- 📨 **Telegram Send Message:** Sends questions, summaries, and operation results to the customer.

### 🧠 Conversation Memory

The memory session must use a stable identifier for each Telegram conversation, such as the Telegram chat ID.

The system must be tested with multiple customers to ensure that their information remains separate and previous answers are available when needed.

## 📋 7. Customer Information Requirements

The agent must collect the following nine fields:

| Field | Description | Requirements |
|---|---|---|
| 🏠 Property type | Requested property type | Apartment, Villa, Commercial |
| 🔑 Buy/Rent | Customer's request | Buy or Rent |
| 🆕 New/Resale | Property condition preference | New, Resale, or Not Applicable |
| ❓ First Ourcase | Customer's answer to this field | Yes, No, or Not Applicable |
| 📅 Timeline | Expected timeframe | One of the approved options |
| 💰 Budget | Customer's budget range | One of the five approved categories |
| 👤 Name | Customer's name | Provided by the customer |
| 📧 Email | Customer's email address | Must have a valid format |
| 📱 Phone Number | Customer's phone number | Provided by the customer |

**📝 Note:** `First Ourcase` is retained exactly as specified in the project requirements. Its intended meaning should be confirmed before changing the field name.

### 📅 Approved Timeline Values

- Immediately
- Within 1 month
- 1–3 months
- 3–6 months
- 6+ months

### 💰 Approved Budget Categories

| Budget Amount | Stored Category |
|---|---|
| Less than $200,000 | Below $200,000 |
| $200,000 to less than $400,000 | $200,000 to below $400,000 |
| $400,000 to less than $700,000 | $400,000 to below $700,000 |
| $700,000 to $1,000,000, inclusive | $700,000 to $1,000,000 |
| More than $1,000,000 | Above $1,000,000 |

⚠️ If the customer's budget is unclear, the agent must ask for clarification instead of guessing.

## ⚙️ 8. Conditional Business Rules

### 🏡 Buying a Property

If the customer selects `Buy`, the agent must collect:

- 🆕 New/Resale
- ❓ First Ourcase

Both fields must be completed before preparing the final summary.

### 🏠 Renting a Property

If the customer selects `Rent`, the agent must:

- ⏭️ Skip the New/Resale question.
- ⏭️ Skip the First Ourcase question.
- ✅ Set both fields to `Not Applicable`.

These rules must be applied before preparing the final summary and saving the data.

## 💬 9. Agent Conversation Flow

### 👋 Step 1: Welcome the Customer

The agent starts the conversation with the following welcome message:

> Hello and welcome to XYZ Real Estate! 🏡
>
> We're delighted to help you find the right property for your needs. Whether you're looking to buy or rent, I'm here to guide you through the process and understand what you're looking for.
>
> To get started, are you looking to buy a property or rent one?

### 📝 Step 2: Collect Information

The agent must:

- 🧠 Understand information provided in natural language.
- 📥 Accept multiple answers in a single message.
- 🔀 Accept information in any order.
- 💾 Remember previously provided answers.
- 🔎 Ask only for missing information.
- ❓ Request clarification when an answer is ambiguous.
- 🚫 Avoid inventing customer information.

### ✅ Step 3: Validate Information

Before preparing the summary, the agent checks that all required fields are complete and valid.

Examples:

- 📧 An invalid email address requires correction.
- 💰 An unclear budget requires clarification.
- 🏠 A rental request sets both conditional fields to `Not Applicable`.
- ✏️ A corrected answer replaces the previous value.

### 🤝 Step 4: Confirm Before Saving

When all required fields are complete, the agent presents a summary containing all nine fields:

1. 🏠 Property type
2. 🔑 Buy/Rent
3. 🆕 New/Resale
4. ❓ First Ourcase
5. 📅 Timeline
6. 💰 Budget
7. 👤 Name
8. 📧 Email
9. 📱 Phone Number

The agent then asks the customer to confirm the information.

If the customer corrects any field, the agent updates the summary and requests confirmation again.

🔒 **No data may be saved merely because the information is complete. Explicit customer confirmation is required.**

### 📊 Step 5: Save the Confirmed Information

After receiving confirmation, the agent uses the Google Sheets tool to save the customer record.

The saved values must match the confirmed summary exactly.

🛡️ The workflow should prevent duplicate rows if the same confirmation or completed request is processed more than once.

### 🔍 Step 6: Verify the Result

After the save operation, the agent checks the actual tool result.

- ✅ **Success:** Inform the customer that the information was saved.
- ❌ **Failure:** Explain that saving was unsuccessful without claiming that the record was saved.

A confirmation message alone is not proof of a successful operation.

## 📊 10. Google Sheets Configuration

Create a Google Spreadsheet named:

`XYZ Real Estate Leads`

Create a worksheet named:

`Leads`

The first row must contain the following nine column headers in the exact order specified.

| Column | Header |
|---|---|
| A | Property type |
| B | Buy/Rent |
| C | New/Resale |
| D | First Ourcase |
| E | Timeline |
| F | Budget |
| G | Name |
| H | Email |
| I | Phone Number |

Each successful submission must add one new row containing exactly these nine fields.

⚠️ No additional data columns should be introduced.

### 🛡️ Data Integrity Requirements

- 🔒 Save only after explicit confirmation.
- ✅ Match saved values to the confirmed summary.
- 📋 Preserve the required column order.
- 🔁 Prevent duplicate entries for the same completed request.
- ⚠️ Handle Google Sheets errors without reporting false success.
- 🔍 Verify the actual spreadsheet contents during testing.

## 🧪 11. Testing Plan

The following scenarios define the required testing coverage. Results must be updated after each test is executed in n8n and verified against Google Sheets.

| ID | Test Scenario | Expected Result |
|---|---|---|
| T01 | 🆕 A new customer starts a conversation | Welcome message is sent and information collection begins |
| T02 | 📝 Customer provides multiple details in one message | All clearly provided details are captured without unnecessary repeated questions |
| T03 | 🔎 Customer provides incomplete information | The agent asks only for missing fields |
| T04 | ❓ Customer gives an ambiguous answer | The agent asks for clarification |
| T05 | 🏠 Customer wants to rent a property | Both conditional fields are set to Not Applicable without asking those questions |
| T06 | 🧠 Customer sends multiple messages | Previous answers remain available |
| T07 | ✏️ Customer corrects an answer | Information is updated and the summary is presented again |
| T08 | 🔒 Information is complete but not confirmed | No row is added to Google Sheets |
| T09 | ✅ Customer confirms the summary | The correct record is saved to the specified columns |
| T10 | ❌ Google Sheets returns an error | The agent does not report successful saving |
| T11 | 🔁 The same confirmation is processed again | No duplicate row is created for the same completed request |
| T12 | 👥 Two customers use the agent simultaneously | Their conversation histories and information remain separate |

### 🔬 Additional Validation Checks

- 📧 Test an invalid email address.
- 💰 Test each budget boundary: $200,000, $400,000, $700,000, and $1,000,000.
- 🔄 Test changing a request from Buy to Rent or from Rent to Buy.
- 📱 Test incomplete or invalid phone numbers according to the implemented validation rules.
- ⚠️ Test a failed or unavailable AI model request.
- ❌ Test a customer who rejects the final summary.
- 🔁 Test a customer who sends a new message after the record has been saved.

### 📸 Testing Evidence

For each scenario, record:

- 🆔 Test ID
- 💬 Input message
- 🤖 Actual agent response
- 🎯 Expected result
- 📋 Actual result
- 📊 Google Sheets verification, where applicable
- ✅/❌ Pass/Fail status
- 🐛 Bug description and fix, if needed

**Testing Status:** To be completed and documented based on actual execution results. A test must not be marked as passed until its expected behavior has been verified.

## ⚠️ 12. Error Handling and Reliability

| Failure | Required Behavior |
|---|---|
| ❓ Invalid customer input | Request clarification or correction |
| 📝 Missing required information | Continue collecting information |
| 🤖 AI model error | Handle the failure without fabricating a response or saving unconfirmed data |
| 🧠 Memory/session issue | Avoid using information from another customer's conversation |
| 📊 Google Sheets failure | Report the failure honestly and support safe recovery |
| 🔁 Repeated confirmation | Avoid duplicate records for the same request |

## 🔐 13. Privacy and Data Protection

The workflow handles personal information, including customer names, email addresses, and phone numbers.

Recommended safeguards include:

- 👥 Use separate memory sessions for each customer.
- 🔒 Limit access to the Google spreadsheet.
- 🔑 Store credentials securely in n8n credentials.
- 🛡️ Avoid exposing customer information in unnecessary logs or error messages.
- 🚫 Do not send data to Google Sheets before confirmation.
- 🔍 Verify that the agent does not mix customer records.

## 📦 14. Project Deliverables

The final project submission should include:

- ⚙️ **n8n Workflow:** The complete automation workflow.
- 📝 **System Prompt:** Agent instructions, validation rules, conditional logic, and tool-use restrictions.
- 📊 **Google Sheets:** A working spreadsheet with the nine required columns.
- 🧪 **Testing Results:** Documented outcomes, including failures and fixes.
- 🎥 **Short Demonstration:** A practical demonstration of information collection, confirmation, saving, and result verification.
- 📄 **README Documentation:** Project overview, architecture, business rules, and testing documentation.

## 🏆 15. Success Criteria

The project is successful when the agent can:

- 💬 Understand customer messages and collect the required information.
- 🧠 Maintain conversation context across multiple messages.
- 🔎 Identify missing information and apply the correct business rules.
- ✅ Validate customer responses without guessing.
- 🤝 Request explicit confirmation before saving.
- 📊 Save confirmed information in the correct Google Sheets columns.
- 🔍 Verify the save result before reporting success.
- 🔁 Prevent duplicate records and isolate different customer sessions.

## 🎓 16. Key Learning Outcomes

This project demonstrates practical experience with:

- 🤖 AI agent design and prompt engineering.
- ⚙️ Workflow automation using n8n.
- 💬 Telegram bot integration.
- 🧠 Conversational memory and session management.
- 📋 Data validation and conditional business logic.
- 🔗 External tool integration.
- 🔒 Controlled execution of actions requiring user confirmation.
- 🧪 Error handling, testing, and data integrity.

## 🚀 Conclusion

XYZ Real Estate AI Agent demonstrates how AI can support a real business process by turning customer conversations into structured, validated, and confirmed lead records.

🎯 The main objective is not simply to connect an AI model to an external tool. It is to build a reliable agent that understands customer needs, follows business rules, requests approval before taking action, and verifies the outcome of every critical operation.
