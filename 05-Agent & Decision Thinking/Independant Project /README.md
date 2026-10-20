# Chaos to Action 🤖📋
### AI-Powered Task Organizer and Execution Assistant

## 📌 Project Overview

**Chaos to Action** is an AI-powered task management assistant built with n8n and Telegram. It helps users transform unorganized messages, ideas, and pending tasks into a clear and structured action plan.

The assistant identifies tasks, assigns priorities, extracts deadlines and statuses, and suggests practical steps to help users start working on the most important task.

## 🎯 Problem Statement

People often have many tasks, messages, and responsibilities but struggle to organize them and decide what to do first.

This can lead to missed deadlines, poor time management, and difficulty tracking progress.

## 💡 Solution

Chaos to Action uses AI and workflow automation to:

- Extract tasks from unstructured messages.
- Organize tasks by priority.
- Identify deadlines and current statuses.
- Highlight the most urgent task and explain why it matters.
- Create a step-by-step execution plan.
- Suggest the current action the user should take.
- Guide the user through the next steps after confirming task completion.
- Store task information in Google Sheets for tracking.

## ✨ Key Features

- **Task Extraction:** Converts unorganized text into clear tasks.
- **Priority Classification:** Categorizes tasks as High, Medium, or Low.
- **Deadline Identification:** Extracts deadlines mentioned in messages.
- **Status Tracking:** Organizes task statuses, such as Not Started.
- **AI-Powered Planning:** Creates practical execution steps.
- **Current Step Guidance:** Tells the user what to do next.
- **Telegram Integration:** Allows users to interact with the assistant through Telegram.
- **Google Sheets Integration:** Stores structured task information.
- **Workflow Automation:** Connects the different steps automatically using n8n.

## ⚙️ How It Works

1. The user sends a message containing tasks or unorganized information through Telegram.
2. The workflow receives the message using the Telegram Trigger.
3. The AI Agent analyzes the message and extracts the relevant tasks.
4. The AI organizes tasks by priority, deadline, and status.
5. The assistant identifies the highest-priority task and prepares an execution plan.
6. The workflow processes and formats the response using a Code node.
7. Task information is stored in Google Sheets using the configured workflow.
8. The assistant sends the organized results back to Telegram.
9. The user can confirm completion by sending **"تم"** to continue to the next step, when the follow-up logic is configured.

## 🛠️ Technologies Used

- **n8n:** Workflow automation and integration.
- **Telegram Bot API:** User interaction and messaging.
- **Google Gemini API:** AI-powered task analysis and planning.
- **Google Sheets:** Task storage and tracking.
- **JavaScript:** Data processing and response formatting.

## 🔄 Workflow Components

| Component | Purpose |
|---|---|
| Telegram Trigger | Receives user messages |
| AI Agent | Analyzes tasks and generates an action plan |
| Code | Processes and formats the AI output |
| Google Sheets | Stores structured task data |
| Telegram Send Message | Sends the final response to the user |

## 📊 Google Sheets Structure

The workflow uses the following columns to organize task information:

| Column | Description |
|---|---|
| Original Message | The original user message |
| Task | The extracted task |
| Priority | High, Medium, or Low |
| Deadline | The identified deadline |
| Status | The current task status |
| Suggested Action | The recommended next action |

Each task should be stored as a separate row to support clear tracking and organization.

## 🧪 Testing

The workflow can be evaluated using the following scenarios:

| Test Scenario | Expected Result |
|---|---|
| Send a message containing multiple tasks | All identifiable tasks are extracted |
| Include different deadlines | Deadlines are assigned to the correct tasks |
| Include urgent and non-urgent tasks | Tasks receive appropriate priority levels |
| Send an unclear task | Missing information is not invented |
| Send a message without a clear deadline | The deadline remains unspecified |
| Process tasks for Google Sheets | Task data is mapped to the correct columns |
| Send the AI response to Telegram | The response is readable and properly formatted |
| Send an empty AI response | The workflow handles the error instead of returning an empty plan |

## 🐛 Issues and Improvements

During development, the workflow required troubleshooting and adjustments.

- **AI API Rate Limit:** Requests could fail when the configured Gemini API quota was exceeded.
- **Task Extraction:** The response-processing logic needed adjustments to preserve the full AI-generated task summary.
- **Telegram Formatting:** Escaped characters and Markdown formatting caused display issues.
- **Telegram Message Parsing:** Special characters could cause Telegram message errors.
- **Response Cleanup:** The output needed formatting improvements to make task summaries easier to read.

These issues highlighted the importance of testing each workflow component and validating the output before sending it to the user.

## 🚀 Future Improvements

- Add interactive task completion and progress tracking.
- Update task statuses automatically after user confirmation.
- Improve error handling and API rate-limit management.
- Add reminders for upcoming deadlines.
- Generate daily or weekly task summaries.
- Improve task storage validation and duplicate detection.
- Support more advanced task filtering and reporting.

## 📁 Project Goal

The goal of Chaos to Action is to demonstrate how AI and workflow automation can improve productivity by transforming scattered information into organized tasks and practical actions.

**From chaos to clarity, and from planning to action.**
